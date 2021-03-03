---
layout: post
title: Proxy Pattern
permalink: /:collection/design-patterns/structural/proxy-pattern
---

- TOC
{:toc}

<hr><br>

-	Provide a ***placeholder for another object to control access to it***.
-	Used ***when we want to provide controlled access of a functionality***.

# Example - Proxy Pattern
-	Let’s say we have a class that can run some command on the system. Now if we are using it, its fine but if we want to give this program to a client application, it can have severe issues because client program can issue command to delete some system files or change some settings that you don’t want.
- Here a proxy class can be created to provide controlled access of the program.

```java
public interface CommandExecutor {
    public void runCommand(String cmd) throws Exception;
}
```
```java
public class CommandExecutorImpl implements CommandExecutor {
    @Override
    public void runCommand(String cmd) throws IOException {
        //some heavy implementation
        Runtime.getRuntime().exec(cmd);
        System.out.println("'" + cmd + "' command executed.");
    }
}
```
Now we want to provide only admin users to have full access of above class, if the user is not admin then only limited commands will be allowed. Here is our very simple proxy class implementation.
```java
public class CommandExecutorProxy implements CommandExecutor {
    private boolean isAdmin;
    private CommandExecutor executor;

    public CommandExecutorProxy(String user, String pwd) {
        if ("Pankaj".equals(user) && "J@urnalD$v".equals(pwd))
            isAdmin = true;
        executor = new CommandExecutorImpl();
    }

    @Override
    public void runCommand(String cmd) throws Exception {
        if (isAdmin) {
            executor.runCommand(cmd);
        } else {
            if (cmd.trim().startsWith("rm")) {
                throw new Exception("rm command is not allowed for non-admin users.");
            } else {
                executor.runCommand(cmd);
            }
        }
    }
}
```
```java
public class TestProxyPattern {
    public static void main(String[] args) {
        CommandExecutor executor = new CommandExecutorProxy("Pankaj", "wrong_pwd");
        try {
            executor.runCommand("ls -ltr");
            executor.runCommand("rm -rf abc.pdf");
        } catch (Exception e) {
            System.out.println("Exception Message::" + e.getMessage());
        }
    }
}

// Output
ls -ltr command executed.
Exception Message::rm command is not allowed for non-admin users.
```

# Common Use-Proxy Pattern
Proxy design pattern common uses are
- to control access.
- to provide a wrapper implementation for better performance.

# JDK Example-Proxy Pattern
- Java RMI package uses proxy pattern.