# Operation Manual

## Staying Up to Date with the Bootcamp's GitHub Repo

### Adding the Bootcamp's Repository as a Remote

1. **Add the Bootcamp's Repository as a Remote**:
   ```sh
   git remote add upstream https://github.com/DataExpert-io/data-engineer-handbook.git
   ```

2. **Fetch the Latest Changes from the Bootcamp's Repository**:
   ```sh
   git fetch upstream
   ```

3. **Merge the Latest Changes into Your Local Branch**:
   ```sh
   git merge upstream/main
   ```

4. **Push the Merged Changes to Your Fork**:
   ```sh
   git push origin main
   ```

### Example Commands

1. **Add the Bootcamp's Repository as a Remote**:
   ```sh
   git remote add upstream https://github.com/DataExpert-io/data-engineer-handbook.git
   ```

2. **Fetch the Latest Changes from the Bootcamp's Repository**:
   ```sh
   git fetch upstream
   ```

3. **Merge the Latest Changes into Your Local Branch**:
   ```sh
   git merge upstream/main
   ```

4. **Push the Merged Changes to Your Fork**:
   ```sh
   git push origin main
   ```

## Automating the Process

To automate the process of staying up to date with the bootcamp's GitHub repo, you can create a script and schedule it using a cron job (on Unix-based systems) or Task Scheduler (on Windows).

### Example Script (update_repo.sh)

```sh
#!/bin/bash

# Navigate to the project directory
cd /path/to/your/project

# Fetch the latest changes from the bootcamp's repository
git fetch upstream

# Merge the latest changes into your local branch
git merge upstream/main

# Push the merged changes to your fork
git push origin main
```

### Scheduling the Script (Cron Job Example)

1. Open the crontab editor:
   ```sh
   crontab -e
   ```

2. Add a new cron job to run the script daily at midnight:
   ```sh
   0 0 * * * /path/to/update_repo.sh
   ```

This will ensure that your fork stays up to date with the bootcamp's GitHub repo automatically.
