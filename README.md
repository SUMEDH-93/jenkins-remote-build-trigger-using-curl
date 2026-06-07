# 🚀 Jenkins Remote Build Trigger Using cURL and Authentication Token

## 🎯 Objective

Trigger a Jenkins job remotely from the terminal using cURL and an authentication token.

## 📋 Prerequisites

* Jenkins Installed and Running
* Build Authorization Token Root Plugin Installed
* Jenkins Job Created (`demo-4th`)

## 🛠️ Steps

### 1. Install Build Authorization Token Root Plugin

* Manage Jenkins → Plugins
* Search **Build Authorization Token Root**
* Install Plugin

### 2. Configure Remote Build Trigger

* Open Job **demo-4th**
* Click **Configure**
* Enable **Trigger builds remotely (e.g., from scripts)**
* Enter Token:

```text
mytoken123
```

### 3. Configure Execute Shell

Add the following commands in **Build Steps → Execute Shell**:

```bash
ls
cat README.md
cat index.html
```

### 4. Save the Job

Click **Save**.

### 5. Reference Remote Build URL Format

```text
buildByToken/build?job=RevolutionTest&token=TacoTuesday
```

### 6. Replace with Job Name and Token

```text
buildByToken/build?job=demo-4th&token=mytoken123
```

### 7. Trigger Build from Terminal

```bash
curl "http://100.31.79.29:8080/buildByToken/build?job=demo-4th&token=mytoken123"
```

## ✅ Verification

1. Open Jenkins Dashboard.
2. Open Job **demo-4th**.
3. Verify a new build is created in Build History.
4. Open Console Output.
5. Verify the following commands executed successfully:

```bash
ls
cat README.md
cat index.html
```

6. Confirm Build Status = Success.

## 🏗️ Workflow

```text
Terminal
   ↓
cURL Request
   ↓
Authentication Token Validation
   ↓
Jenkins Receives Request
   ↓
demo-4th Job Triggered
   ↓
Execute Shell Runs
   ↓
Build Successful
```

## 🎉 Result

The Jenkins job was successfully triggered remotely using a #CURL command and authentication token.
