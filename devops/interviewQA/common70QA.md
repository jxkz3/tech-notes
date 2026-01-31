# DEVOPS INTERN INTERVIEW - 70 Q&A

## LINUX (20 Questions)

1. What is Linux?
   Linux is an open-source operating system used widely in servers and development.

2. How to check disk space?
   df -h shows disk space for all mounted filesystems.

3. How to check memory usage?
   free -h shows total, used, and free memory.

4. How to check CPU usage?
   top or htop shows real-time CPU usage by processes.

5. How to find a file by name?
   find /path -name "filename" searches for files.

6. How to view file contents?
   cat filename shows entire file, less filename shows page by page.

7. How to create a directory?
   mkdir dirname creates a new directory.

8. How to remove a file or directory?
   rm filename removes file, rm -r dirname removes directory.

9. How to copy files?
   cp source destination copies files or directories.

10. How to move/rename files?
    mv oldname newname renames or moves files.

11. What are file permissions?
    Three types: read(r), write(w), execute(x) for user, group, others.

12. What does chmod 755 mean?
    Owner can read/write/execute (7), group and others can read/execute (5).

13. How to change file owner?
    chown user:group filename changes ownership.

14. What is a process?
    A running program instance with its own memory space.

15. How to list running processes?
    ps aux shows all running processes.

16. How to kill a process?
    kill PID sends termination signal, kill -9 PID forces immediate stop.

17. What is a daemon?
    A background service that runs continuously.

18. How to check system logs?
    journalctl shows system logs, /var/log/ contains log files.

19. What is grep?
    Searches for text patterns in files: grep "pattern" filename.

20. What is cron?
    Schedules tasks to run automatically at specified times.

## GIT (10 Questions)

21. What is Git?
    A version control system that tracks changes to code.

22. What is GitHub?
    A platform for hosting Git repositories online.

23. How to initialize a Git repository?
    git init creates a new Git repository.

24. How to stage files?
    git add filename stages changes for commit.

25. How to commit changes?
    git commit -m "message" saves changes with a message.

26. How to check status?
    git status shows changed files and staging status.

27. What is a branch?
    A separate line of development from main code.

28. How to create a branch?
    git branch branchname creates new branch.

29. How to merge branches?
    git merge branchname merges branch into current branch.

30. What is .gitignore?
    A file listing files/folders Git should ignore.

## DOCKER (15 Questions)

31. What is Docker?
    A platform for running applications in containers.

32. What is a container?
    A lightweight, standalone package with an app and its dependencies.

33. What is a Docker image?
    A read-only template used to create containers.

34. What is a Dockerfile?
    A text file with instructions to build a Docker image.

35. How to build an image?
    docker build -t imagename . builds image from Dockerfile.

36. How to run a container?
    docker run imagename creates and starts a container.

37. How to list containers?
    docker ps shows running containers, docker ps -a shows all.

38. How to stop a container?
    docker stop containerid stops a running container.

39. How to remove a container?
    docker rm containerid removes a stopped container.

40. How to see container logs?
    docker logs containerid shows container output.

41. How to enter a running container?
    docker exec -it containerid /bin/bash opens shell inside container.

42. What is Docker Compose?
    A tool to define and run multi-container applications.

43. What are Docker volumes?
    Persistent storage for containers to save data.

44. How to expose ports in Docker?
    docker run -p 8080:80 maps host port 8080 to container port 80.

45. What is Docker Hub?
    A registry for sharing Docker images publicly.

## CI/CD (10 Questions)

46. What is CI/CD?
    Continuous Integration and Continuous Deployment/Delivery.

47. What is Continuous Integration?
    Automatically building and testing code when changes are made.

48. What is Continuous Deployment?
    Automatically deploying code to production after tests pass.

49. What is Jenkins?
    An automation server for building CI/CD pipelines.

50. What is GitHub Actions?
    GitHub's built-in CI/CD automation tool.

51. What is a pipeline?
    A series of automated steps for building, testing, deploying.

52. What is a build?
    The process of compiling code into executable form.

53. What is testing in CI/CD?
    Automated tests that run to check code works correctly.

54. What is deployment?
    Releasing code to servers for users to access.

55. What is rollback?
    Reverting to a previous stable version if deployment fails.

## NETWORKING (10 Questions)

56. What is TCP/IP?
    Protocols for communication over networks.

57. What is HTTP?
    Protocol for transferring web pages (port 80).

58. What is HTTPS?
    Secure HTTP with encryption (port 443).

59. What is DNS?
    Translates domain names to IP addresses.

60. What is a port?
    A numbered endpoint for network connections.

61. What is localhost?
    127.0.0.1 - refers to the current computer.

62. What is ping?
    Tests connectivity to another computer.

63. What is curl?
    Command-line tool for making HTTP requests.

64. What is SSH?
    Secure Shell for remote server access.

65. What is a firewall?
    Controls network traffic to/from a system.

## CLOUD & DEVOPS CONCEPTS (5 Questions)

66. What is cloud computing?
    Using remote servers over internet instead of local machines.

67. What is AWS?
    Amazon Web Services, a cloud platform.

68. What is Kubernetes?
    A system for managing containerized applications.

69. What is monitoring?
    Watching systems to ensure they're working properly.

70. What is DevOps?
    A practice combining development and operations for faster delivery.
