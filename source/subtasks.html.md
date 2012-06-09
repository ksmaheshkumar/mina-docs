---
title: Subtasks
order: 5
group: Getting started
---

Mina provides the helper `invoke` to invoke other tasks from a
task.

    task :down do
      invoke :maintenance_on
      invoke :restart
    end

    task :maintenance_on
      queue 'touch maintenance.txt'
    end

    task :restart
      queue 'sudo service restart apache'
    end

In this example above, if you type `mina down`, it simply invokes the other
subtasks which queues up their commands. The commands will be ran after
everything.