# FINAL ROUND DEVOPS INTERN INTERVIEW - 100 Q&A

## PART 1: PROBLEM-SOLVING SCENARIOS (20 Questions)

1. Q: You get an alert that a production website is down. What's your first 3 steps?
   A: 1. Check if I can access it (ping/curl) 2. Check server resources (CPU/memory) 3. Check error logs

2. Q: A deployment just failed. How would you investigate?
   A: 1. Check deployment logs 2. Check recent code changes 3. Roll back to working version 4. Fix issue and retry

3. Q: Users report the website is slow. How would you diagnose?
   A: Check server resources, database performance, network speed, and look for traffic spikes or errors

4. Q: Database connection errors suddenly appear. Your approach?
   A: Check if DB service is running, verify credentials, check network, look at connection limits

5. Q: Disk space is running low on a server. How to handle?
   A: Find large files with du, clean old logs/temp files, archive old data, add more storage

6. Q: A service keeps restarting. How to debug?
   A: Check service logs, look for error messages, check resource limits, test configuration

7. Q: SSH connection to server fails. What to check?
   A: Check if server is on, SSH service running, firewall rules, credentials, and server logs

8. Q: How would you monitor a new application?
   A: Set up health checks, monitor resources, track errors and response times, create dashboards

9. Q: DNS resolution is failing. Troubleshooting steps?
   A: Check internet, try different DNS servers, check local DNS config, verify domain status

10. Q: How to ensure zero downtime during deployment?
    A: Use blue-green deployment, health checks before switching, rolling updates, automated rollback

11. Q: How to handle a security vulnerability in a dependency?
    A: Check if affected, update to fixed version, test in staging, deploy to production, monitor

12. Q: CI/CD pipeline is taking too long. How to optimize?
    A: Run tasks in parallel, cache dependencies, remove unnecessary steps, use faster machines

13. Q: How to manage different environments (dev, staging, prod)?
    A: Separate infrastructure for each, version control for configs, environment variables, automate creation

14. Q: Application logs are growing too large. Solution?
    A: Implement log rotation, archive old logs, use centralized logging, set retention policies

15. Q: How to secure server access?
    A: Use SSH keys instead of passwords, disable root login, use firewall, regular updates, minimal access

16. Q: Backup strategy for important data?
    A: Regular automated backups, test restores, offsite storage, versioned backups, monitoring

17. Q: How to scale an application that's getting more users?
    A: Add more servers, use load balancer, optimize database, cache frequently used data

18. Q: SSL certificate is expiring soon. What to do?
    A: Renew certificate before expiry, test new certificate, update on all servers, set reminder for next renewal

19. Q: How to handle configuration across multiple servers?
    A: Use configuration management tools, version control, central configuration, automated deployment

20. Q: Developer says "It works on my machine". How to resolve?
    A: Ensure same environment everywhere, use containers, same dependencies, proper testing in staging

## PART 2: LINUX FUNDAMENTALS (20 Questions)

21. Q: How to check running processes?
    A: ps aux or top or htop

22. Q: How to check disk usage?
    A: df -h for disk space, du -sh for directory size

23. Q: How to find a file by name?
    A: find /path -name "filename"

24. Q: How to check memory usage?
    A: free -h or top

25. Q: How to view the end of a log file?
    A: tail -f filename (follow) or tail -n 50 filename (last 50 lines)

26. Q: What does chmod 644 mean?
    A: Owner can read/write, group can read, others can read

27. Q: How to create a new user?
    A: useradd username and passwd username

28. Q: How to check network connections?
    A: netstat -tulpn or ss -tulpn

29. Q: How to search text in files?
    A: grep "text" filename

30. Q: How to schedule a daily backup?
    A: Add to crontab: 0 2 \* \* \* backup-command

31. Q: How to check system uptime?
    A: uptime command

32. Q: How to compress a directory?
    A: tar -czvf archive.tar.gz directory/

33. Q: How to extract a tar file?
    A: tar -xzvf archive.tar.gz

34. Q: How to check kernel version?
    A: uname -r

35. Q: How to list all installed packages?
    A: dpkg -l (Debian/Ubuntu) or rpm -qa (RedHat/CentOS)

36. Q: How to update all packages?
    A: apt update && apt upgrade (Ubuntu) or yum update (CentOS)

37. Q: How to check service status?
    A: systemctl status servicename

38. Q: How to restart a service?
    A: systemctl restart servicename

39. Q: How to change file permissions?
    A: chmod permissions filename

40. Q: How to change file owner?
    A: chown user:group filename

## PART 3: NETWORKING (15 Questions)

41. Q: What is TCP vs UDP?
    A: TCP is reliable (web, email), UDP is fast (video, games)

42. Q: What is DNS?
    A: Translates domain names (google.com) to IP addresses (8.8.8.8)

43. Q: What is HTTP vs HTTPS?
    A: HTTP is normal web traffic, HTTPS is encrypted HTTP

44. Q: What is port 80 used for?
    A: HTTP web traffic

45. Q: What is port 443 used for?
    A: HTTPS secure web traffic

46. Q: What is port 22 used for?
    A: SSH remote access

47. Q: What is localhost?
    A: 127.0.0.1 - refers to the current computer

48. Q: How to test network connectivity?
    A: ping hostname or ip-address

49. Q: What is a firewall?
    A: Controls allowed network traffic to/from a system

50. Q: What is SSH?
    A: Secure Shell for remote server access

51. Q: What is curl used for?
    A: Command line tool to make HTTP requests

52. Q: What is a load balancer?
    A: Distributes traffic across multiple servers

53. Q: What is a reverse proxy?
    A: Sits in front of servers and forwards requests

54. Q: What is VPN?
    A: Virtual Private Network for secure remote access

55. Q: How to check open ports?
    A: netstat -tulpn or ss -tulpn

## PART 4: GIT & VERSION CONTROL (10 Questions)

56. Q: What is Git?
    A: Version control system to track code changes

57. Q: How to clone a repository?
    A: git clone repository-url

58. Q: How to commit changes?
    A: git add filename then git commit -m "message"

59. Q: How to push to remote?
    A: git push origin branchname

60. Q: How to pull latest changes?
    A: git pull

61. Q: What is a branch?
    A: Separate line of development

62. Q: How to create a branch?
    A: git branch new-branch

63. Q: How to switch branches?
    A: git checkout branchname

64. Q: How to merge branches?
    A: git merge branchname

65. Q: What is .gitignore?
    A: File that lists files Git should ignore

## PART 5: CI/CD CONCEPTS (15 Questions)

66. Q: What is CI/CD?
    A: Continuous Integration and Continuous Deployment

67. Q: What is Continuous Integration?
    A: Automatically building and testing code changes

68. Q: What is Continuous Deployment?
    A: Automatically deploying tested code to production

69. Q: Why use CI/CD?
    A: Faster releases, fewer bugs, automated testing

70. Q: What are pipeline stages?
    A: Build → Test → Deploy → Monitor

71. Q: What is a build failure?
    A: When code compilation or tests fail in CI

72. Q: What is automated testing?
    A: Tests that run automatically without manual effort

73. Q: What is deployment rollback?
    A: Reverting to previous working version

74. Q: What are environment variables in CI/CD?
    A: Configuration values that change per environment

75. Q: What is version tagging?
    A: Marking specific code versions for deployment

76. Q: What is canary deployment?
    A: Rolling out to small user group first, then all

77. Q: What is infrastructure testing?
    A: Testing infrastructure code before applying

78. Q: What is pipeline as code?
    A: Defining CI/CD pipeline in configuration files

79. Q: What are build artifacts?
    A: Output files from build process (binaries, packages)

80. Q: What is deployment verification?
    A: Checking deployment was successful

## PART 6: DEVOPS TOOLS & CONCEPTS (20 Questions)

81. Q: What is Docker?
    A: Platform for running applications in containers

82. Q: What is a container?
    A: Lightweight package with app and dependencies

83. Q: How to build Docker image?
    A: docker build -t imagename .

84. Q: How to run Docker container?
    A: docker run imagename

85. Q: What is Docker Compose?
    A: Tool to define and run multi-container apps

86. Q: What are Docker volumes?
    A: Persistent storage for containers

87. Q: What is Kubernetes?
    A: System for managing containerized applications

88. Q: What is a pod in Kubernetes?
    A: Smallest unit, can contain one or more containers

89. Q: What is Terraform?
    A: Tool for Infrastructure as Code

90. Q: What is Ansible?
    A: Configuration management and automation tool

91. Q: What is Jenkins?
    A: Automation server for CI/CD pipelines

92. Q: What is monitoring?
    A: Watching systems to ensure they work properly

93. Q: What is logging?
    A: Recording events for debugging and auditing

94. Q: What is alerting?
    A: Notifications when something goes wrong

95. Q: What is cloud computing?
    A: Using remote servers over internet

96. Q: What is AWS/Azure/GCP?
    A: Cloud service providers

97. Q: What is Infrastructure as Code?
    A: Managing infrastructure using configuration files

98. Q: What is configuration management?
    A: Automating system setup and configuration

99. Q: What is auto-scaling?
    A: Automatically adding/removing servers based on load

100.  Q: What is the DevOps mindset?
      A: Collaboration, automation, continuous improvement, shared responsibility
