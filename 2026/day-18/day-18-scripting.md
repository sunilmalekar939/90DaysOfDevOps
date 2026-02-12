Day 18 – Shell Scripting: Functions & Advanced Concepts
🔹 Task 1: Basic Functions
File: functions.sh
#!/bin/bash

greet() {
    echo "Hello, $1!"
}

add() {
    local sum=$(( $1 + $2 ))
    echo "Sum is: $sum"
}

# Calling functions
greet "Sunil"
add 10 20

Output
Hello, Sunil!
Sum is: 30

🔹 Task 2: Functions with Return Values
File: disk_check.sh
#!/bin/bash

check_disk() {
    echo "Disk Usage:"
    df -h /
}

check_memory() {
    echo "Memory Usage:"
    free -h
}

main() {
    check_disk
    echo "----------------------"
    check_memory
}

main

Output (Example)
Disk Usage:
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   10G   38G  22% /

----------------------

Memory Usage:
              total   used   free
Mem:           2.0G   800M   1.2G

🔹 Task 3: Strict Mode – set -euo pipefail
File: strict_demo.sh
#!/bin/bash
set -euo pipefail

echo "Testing strict mode..."

# Undefined variable (will fail due to -u)
# echo $UNDEFINED_VAR

# Command failure (will exit due to -e)
# false

# Pipeline failure
# grep "text" non_existing_file | sort

echo "Script completed."

What Each Flag Does
set -e

Exit immediately if any command fails.

set -u

Exit if an undefined variable is used.

set -o pipefail

If any command in a pipeline fails, the whole pipeline fails.

Why This Matters

Prevents silent failures in production automation.

🔹 Task 4: Local Variables
File: local_demo.sh
#!/bin/bash

demo_local() {
    local VAR="I am local"
    echo "Inside function: $VAR"
}

demo_global() {
    VAR2="I am global"
}

demo_local
echo "Outside function: ${VAR:-Not Accessible}"

demo_global
echo "Outside function: $VAR2"

Output
Inside function: I am local
Outside function: Not Accessible
Outside function: I am global

Explanation

local restricts variable scope to function

Global variables remain accessible outside

Best Practice → Always use local inside functions

🔹 Task 5: System Info Reporter
File: system_info.sh
#!/bin/bash
set -euo pipefail

print_header() {
    echo "================================="
    echo "$1"
    echo "================================="
}

system_info() {
    print_header "System Information"
    echo "Hostname: $(hostname)"
    echo "OS: $(uname -a)"
}

uptime_info() {
    print_header "Uptime"
    uptime
}

disk_info() {
    print_header "Top 5 Disk Usage"
    df -h | sort -k5 -r | head -n 6
}

memory_info() {
    print_header "Memory Usage"
    free -h
}

cpu_info() {
    print_header "Top 5 CPU Processes"
    ps -eo pid,comm,%cpu --sort=-%cpu | head -n 6
}

main() {
    system_info
    uptime_info
    disk_info
    memory_info
    cpu_info
}

main

Sample Output (Formatted)
=================================
System Information
=================================
Hostname: ubuntu
OS: Linux ubuntu 5.15.0-...

=================================
Uptime
=================================
 10:32:11 up 2 days,  3:10

=================================
Memory Usage
=================================
              total   used   free
Mem:           2.0G   800M   1.2G

🔹 What I Learned

Functions make scripts modular and reusable.

Strict mode prevents silent automation failures.

Local variables improve script reliability.

Organizing scripts with a main function improves readability.

Production-grade scripts require proper error handling.

🔥 Real DevOps Relevance

CI/CD automation

Monitoring scripts

Health-check tools

Deployment pipelines

Infrastructure reporting

🔹 Interview-Ready Concepts

Why use strict mode?

It prevents hidden failures and makes scripts production-safe.

Why use local variables?

To avoid variable conflicts and unexpected behavior.

Why use main()?

Improves readability and structure in large scripts.
