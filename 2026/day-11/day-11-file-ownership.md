####
# Day 11 Challenge

## Files & Directories Created

- devops-file.txt
- team-notes.txt
- project-config.yaml
- app-logs/
- heist-project/
- bank-heist/

## Ownership Changes

- devops-file.txt: sunil:sunil → berlin:sunil
- team-notes.txt: sunil:sunil → sunil:heist-team
- project-config.yaml → professor:heist-team
- app-logs/ → berlin:heist-team
- heist-project/ → professor:planners (recursive)
- access-codes.txt → tokyo:vault-team
- blueprints.pdf → berlin:tech-team
- escape-plan.txt → nairobi:vault-team

## Commands Used

- ls -l
- chown
- chgrp
- chown -R
- useradd
- groupadd
- mkdir
- touch

## What I Learned

1. File ownership controls who can manage files.
2. chown can change both owner and group together.
3. Recursive (-R) is critical for managing entire application directories.
