# GitHub Actions - Build Only Modified Files Using dorny/paths-filter

---

## **What is dorny/paths-filter?**

```
dorny/paths-filter is a GitHub Action that:
  ✓ Detects which files changed
  ✓ Groups changes by path patterns
  ✓ Outputs true/false for each path
  ✓ Skips unnecessary jobs
  ✓ Speeds up CI/CD pipeline
```

---

## **How It Works**

### **Simple Flow**

```
Developer pushes code
        ↓
GitHub Actions triggered
        ↓
dorny/paths-filter analyzes changed files
        ↓
Matches files against path patterns
        ↓
Outputs true/false for each filter
        ↓
Jobs run only if their filter is true
        ↓
Result: Only necessary jobs run
```

### **Example**

```
Changed Files:
  - src/backend/api.js ✓
  - src/frontend/App.js ✓
  - tests/unit.test.js ✓

Path Filters:
  - backend: 'src/backend/**' → true (match found)
  - frontend: 'src/frontend/**' → true (match found)
  - tests: 'tests/**' → true (match found)

Result:
  - build-backend: runs ✅
  - build-frontend: runs ✅
  - run-tests: runs ✅
```

---

## **Alternative Scenario**

```
Changed Files:
  - README.md
  - package.json

Path Filters:
  - backend: 'src/backend/**' → false (no match)
  - frontend: 'src/frontend/**' → false (no match)
  - docker: 'Dockerfile' → false (no match)

Result:
  - build-backend: skipped ⏭️
  - build-frontend: skipped ⏭️
  - build-docker: skipped ⏭️
  - All jobs skipped, saves time! ⚡
```

---

## **Complete Workflow File**

```yaml
# .github/workflows/build-filtered.yml
name: Build Filtered Files

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  # STEP 1: Detect Changes
  changes:
    runs-on: ubuntu-latest
    outputs:
      backend: ${{ steps.filter.outputs.backend }}
      frontend: ${{ steps.filter.outputs.frontend }}
      docker: ${{ steps.filter.outputs.docker }}
      tests: ${{ steps.filter.outputs.tests }}
    
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3
      
      - name: Filter Paths
        uses: dorny/paths-filter@v2
        id: filter
        with:
          filters: |
            backend:
              - 'src/backend/**'
              - 'src/api/**'
            frontend:
              - 'src/frontend/**'
              - 'src/ui/**'
            docker:
              - 'Dockerfile'
              - 'docker-compose.yml'
            tests:
              - 'tests/**'
              - '**/*.test.js'

  # STEP 2: Build Backend (only if backend files changed)
  build-backend:
    needs: changes
    if: needs.changes.outputs.backend == 'true'
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      
      - name: Install Dependencies
        run: npm install
      
      - name: Build Backend
        run: npm run build:backend
      
      - name: Upload Artifact
        uses: actions/upload-artifact@v3
        with:
          name: backend-build
          path: dist/backend/

  # STEP 3: Build Frontend (only if frontend files changed)
  build-frontend:
    needs: changes
    if: needs.changes.outputs.frontend == 'true'
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      
      - name: Install Dependencies
        run: npm install
      
      - name: Build Frontend
        run: npm run build:frontend
      
      - name: Upload Artifact
        uses: actions/upload-artifact@v3
        with:
          name: frontend-build
          path: dist/frontend/

  # STEP 4: Build Docker (only if Dockerfile changed)
  build-docker:
    needs: changes
    if: needs.changes.outputs.docker == 'true'
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3
      
      - name: Build Docker Image
        run: docker build -t my-app:${{ github.sha }} .
      
      - name: Tag Docker Image
        run: docker tag my-app:${{ github.sha }} my-app:latest
      
      - name: Push Docker Image
        run: |
          # docker login
          # docker push my-app:${{ github.sha }}
          # docker push my-app:latest
          echo "Docker image built and tagged"

  # STEP 5: Run Tests (only if test files changed)
  run-tests:
    needs: changes
    if: needs.changes.outputs.tests == 'true'
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      
      - name: Install Dependencies
        run: npm install
      
      - name: Run Tests
        run: npm test
      
      - name: Upload Coverage
        uses: actions/upload-artifact@v3
        with:
          name: coverage-report
          path: coverage/
```

---

## **Detailed Explanation - Line by Line**

### **PART 1: Job Name and Triggers**

```yaml
name: Build Filtered Files

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]
```

**What it does:**
- `name`: Name of the workflow (shows in GitHub Actions tab)
- `on`: When to trigger this workflow
- `push: branches: [main, develop]`: Trigger when pushing to main or develop
- `pull_request: branches: [main]`: Trigger when creating PR to main

---

### **PART 2: Changes Detection Job**

```yaml
jobs:
  changes:
    runs-on: ubuntu-latest
    outputs:
      backend: ${{ steps.filter.outputs.backend }}
      frontend: ${{ steps.filter.outputs.frontend }}
      docker: ${{ steps.filter.outputs.docker }}
      tests: ${{ steps.filter.outputs.tests }}
```

**What it does:**
- `changes`: Job name that detects file changes
- `runs-on: ubuntu-latest`: Runs on Ubuntu Linux
- `outputs`: Exposes values to other jobs
  - `backend`: true/false if backend files changed
  - `frontend`: true/false if frontend files changed
  - `docker`: true/false if docker files changed
  - `tests`: true/false if test files changed

**How to use outputs in other jobs:**
```yaml
needs.changes.outputs.backend  # Access backend output
needs.changes.outputs.frontend # Access frontend output
```

---

### **PART 3: Checkout Step**

```yaml
steps:
  - name: Checkout Code
    uses: actions/checkout@v3
```

**What it does:**
- Downloads your repository code
- `v3`: Version of the action
- Required before running any build commands

---

### **PART 4: Filter Paths**

```yaml
- name: Filter Paths
  uses: dorny/paths-filter@v2
  id: filter
  with:
    filters: |
      backend:
        - 'src/backend/**'
        - 'src/api/**'
      frontend:
        - 'src/frontend/**'
        - 'src/ui/**'
      docker:
        - 'Dockerfile'
        - 'docker-compose.yml'
      tests:
        - 'tests/**'
        - '**/*.test.js'
```

**What it does:**
- `uses: dorny/paths-filter@v2`: Uses the paths-filter action
- `id: filter`: Identifier to reference outputs
- `filters`: Define path patterns to match

**How filters work:**

```
Filter: backend
Patterns:
  - 'src/backend/**'  (all files in src/backend and subdirs)
  - 'src/api/**'      (all files in src/api and subdirs)

If any changed file matches → backend = true
If no match → backend = false
```

**Wildcard Patterns:**
```
'src/backend/**'       → matches all files under src/backend/
'src/**/*.js'          → matches all .js files under src/
'Dockerfile'           → matches exactly this file
'**/*.test.js'         → matches all .test.js files anywhere
'tests/**'             → matches all files under tests/
```

---

### **PART 5: Build Backend Job**

```yaml
build-backend:
  needs: changes
  if: needs.changes.outputs.backend == 'true'
  runs-on: ubuntu-latest
```

**What it does:**
- `needs: changes`: Wait for `changes` job to complete first
- `if: needs.changes.outputs.backend == 'true'`: Run ONLY if backend files changed
- `runs-on: ubuntu-latest`: Run on Ubuntu

**Logic:**
```
If backend changed → Run build-backend job
If backend NOT changed → Skip this job ⏭️
```

---

### **PART 6: Build Backend Steps**

```yaml
steps:
  - name: Checkout Code
    uses: actions/checkout@v3
  
  - name: Setup Node.js
    uses: actions/setup-node@v3
    with:
      node-version: '18'
  
  - name: Install Dependencies
    run: npm install
  
  - name: Build Backend
    run: npm run build:backend
  
  - name: Upload Artifact
    uses: actions/upload-artifact@v3
    with:
      name: backend-build
      path: dist/backend/
```

**Step Breakdown:**

1. **Checkout Code**
   - Download repository

2. **Setup Node.js**
   - Install Node.js version 18
   - Required to run npm commands

3. **Install Dependencies**
   - Runs: `npm install`
   - Installs all packages from package.json

4. **Build Backend**
   - Runs: `npm run build:backend`
   - Your custom build command
   - Compiles/bundles backend code

5. **Upload Artifact**
   - Saves built files
   - `name: backend-build`: Artifact name
   - `path: dist/backend/`: Location to save

---

### **PART 7: Build Frontend Job**

```yaml
build-frontend:
  needs: changes
  if: needs.changes.outputs.frontend == 'true'
  runs-on: ubuntu-latest
  
  steps:
    # Same structure as backend job
    - name: Checkout Code
      uses: actions/checkout@v3
    
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
    
    - name: Install Dependencies
      run: npm install
    
    - name: Build Frontend
      run: npm run build:frontend
    
    - name: Upload Artifact
      uses: actions/upload-artifact@v3
      with:
        name: frontend-build
        path: dist/frontend/
```

**Difference from backend:**
- `if: needs.changes.outputs.frontend == 'true'`: Check frontend changes
- `run: npm run build:frontend`: Build frontend instead
- `path: dist/frontend/`: Different output path

---

### **PART 8: Build Docker Job**

```yaml
build-docker:
  needs: changes
  if: needs.changes.outputs.docker == 'true'
  runs-on: ubuntu-latest
  
  steps:
    - name: Checkout Code
      uses: actions/checkout@v3
    
    - name: Build Docker Image
      run: docker build -t my-app:${{ github.sha }} .
    
    - name: Tag Docker Image
      run: docker tag my-app:${{ github.sha }} my-app:latest
    
    - name: Push Docker Image
      run: |
        # docker login
        # docker push my-app:${{ github.sha }}
        # docker push my-app:latest
        echo "Docker image built and tagged"
```

**What it does:**
- `if: needs.changes.outputs.docker == 'true'`: Only if Dockerfile changed
- `docker build -t my-app:${{ github.sha }} .`: Build image with unique tag
  - `${{ github.sha }}`: Unique commit SHA
- `docker tag`: Create `latest` tag pointing to this build
- `docker push`: Upload to Docker registry (commented out, uncomment to use)

**${{ github.sha }} Explanation:**
```
Commit SHA: abc123def456
Image tag: my-app:abc123def456
Also tags: my-app:latest

Allows tracking which commit produced which image
```

---

### **PART 9: Run Tests Job**

```yaml
run-tests:
  needs: changes
  if: needs.changes.outputs.tests == 'true'
  runs-on: ubuntu-latest
  
  steps:
    - name: Checkout Code
      uses: actions/checkout@v3
    
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
    
    - name: Install Dependencies
      run: npm install
    
    - name: Run Tests
      run: npm test
    
    - name: Upload Coverage
      uses: actions/upload-artifact@v3
      with:
        name: coverage-report
        path: coverage/
```

**What it does:**
- `if: needs.changes.outputs.tests == 'true'`: Only if test files changed
- `npm test`: Run test suite
- `Upload Coverage`: Save test coverage report

---

## **How to Use This Workflow**

### **Step 1: Create Workflow File**

```bash
mkdir -p .github/workflows
touch .github/workflows/build-filtered.yml
```

### **Step 2: Copy the Complete Workflow**

Paste the complete workflow code from above into the file.

### **Step 3: Customize Path Patterns**

Update the filters to match your project structure:

```yaml
filters: |
  backend:
    - 'src/backend/**'    # Change to your backend path
    - 'src/api/**'
  frontend:
    - 'src/frontend/**'   # Change to your frontend path
    - 'src/ui/**'
  docker:
    - 'Dockerfile'        # Your docker files
    - 'docker-compose.yml'
  tests:
    - 'tests/**'          # Your test directory
    - '**/*.test.js'
```

### **Step 4: Update Build Commands**

Change the `run` commands to match your project:

```yaml
# For Python backend
- name: Build Backend
  run: python -m build

# For Java
- name: Build Backend
  run: mvn clean package

# For multiple languages
- name: Build Backend
  run: |
    cd backend
    npm install
    npm run build
```

### **Step 5: Push to GitHub**

```bash
git add .github/workflows/build-filtered.yml
git commit -m "Add smart build workflow"
git push origin main
```

### **Step 6: Verify**

```
GitHub Repo → Actions tab
You should see "Build Filtered Files" workflow running
```

---

## **Real-World Example - Project Structure**

```
my-project/
├── src/
│   ├── backend/
│   │   ├── api.js
│   │   ├── db.js
│   │   └── utils.js
│   ├── frontend/
│   │   ├── App.js
│   │   ├── Components.js
│   │   └── styles.css
│   └── ui/
│       └── Layout.js
├── tests/
│   ├── backend.test.js
│   ├── frontend.test.js
│   └── integration.test.js
├── Dockerfile
├── docker-compose.yml
├── package.json
├── README.md
└── .github/
    └── workflows/
        └── build-filtered.yml
```

---

## **Example Scenarios**

### **Scenario 1: Only Backend Files Changed**

```
Changed files:
  ✓ src/backend/api.js
  ✓ src/backend/db.js

Result:
  ✓ build-backend → RUNS
  ✗ build-frontend → SKIPPED
  ✗ build-docker → SKIPPED
  ✗ run-tests → SKIPPED

Time saved: 3 jobs skipped! ⚡
```

### **Scenario 2: Only Documentation Changed**

```
Changed files:
  ✓ README.md
  ✓ CHANGELOG.md

Result:
  ✗ build-backend → SKIPPED
  ✗ build-frontend → SKIPPED
  ✗ build-docker → SKIPPED
  ✗ run-tests → SKIPPED

Time saved: All jobs skipped! ⚡⚡⚡
```

### **Scenario 3: Dockerfile Changed**

```
Changed files:
  ✓ Dockerfile

Result:
  ✗ build-backend → SKIPPED
  ✗ build-frontend → SKIPPED
  ✓ build-docker → RUNS
  ✗ run-tests → SKIPPED

Time saved: 3 jobs skipped! ⚡
```

### **Scenario 4: Multiple Areas Changed**

```
Changed files:
  ✓ src/backend/api.js
  ✓ src/frontend/App.js
  ✓ tests/unit.test.js

Result:
  ✓ build-backend → RUNS
  ✓ build-frontend → RUNS
  ✗ build-docker → SKIPPED
  ✓ run-tests → RUNS

Time saved: 1 job skipped! ⚡
```
