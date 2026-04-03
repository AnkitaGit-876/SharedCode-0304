## Overview
You have access to the `sf` terminal command for Salesforce CLI operations. Commit & Merge the components I specify in package.xml to the target branch following this detailed process.
This workflow allows developers to:
- Check the git status
- Validate the modified metadata components added in package.xml against a target Salesforce org.
- If validation succeeds, stage the changes
- Commit the changes with the user-provided commit message
- Push the changes

## Workflow Steps

### 1. Check status of current branch

    ```bash
    git status
    ```
### 2. Validate the changes before staging the changes

    ```bash
    sf project deploy start \
    --target-org ankitam@agentforcevibes.com \
    --manifest package.xml \
    #--source-dir force-app/main/default/classes/APIC1.cls \
    --dry-run 
    ```

    if [ $? -eq 0 ]; then
        echo "✅ VALIDATION SUCCESS"
        exit 0
    else
        echo "❌ VALIDATION FAILED"
        exit 1
    fi

### 3. If validation succeeds, stage the changes

        ```bash
        #git add force-app/main/default/classes/APIC1.cls
        git add ./
        ``` 

### 3. Commit the changes
        Get the commit message from the user and replace it instead of testCommit.
        ```bash
        git commit -m "testCommit"
        ```   

### 4. Push the changes in the branch

        ```bash
        git push
        ```

### 5. End the task and workflow

        End task
