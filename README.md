# taskdata
a taskwarrior utility program to directly manipulate task *.data files

status: imaginary

Taskwarrior (http://taskwarrior.org) users have long asked questions about ID#s changing or not changing, and about archiving tasks that are deleted, to another file. This imaginary program seeks to address this sort of action, and adds a few as well, bu directly manipulating the contents and sequence of the core taskdata files; pending.data, completed.data, undo.data and backlog.data. This is not to be taken lightly! Manipulating the core data set presents a risk of data-loss, and threatens to confuse the task-sync and undo logic.. 

but STILL I'd like go ahead and describe this imaginary program as though the data-integrity and task-sync/undo issues were all taken care of. For the purposes of discussion, please put those concerns on hold, and imagine;

<pre>
usage:

  taskdata [filter] command

commands;
  backup                            (copies all 4 data files +.taskrc to a dated-taskdata.gz (or .zip) file)
  revert [source-file]              (overwrites taskdata files with dated-taskdate.gz (defaults to newest))
  check [target-file]               (tests data files for errors, format compliance, dupe-uuids, etc)
  < filter > archive [target-file]  (matching tasks removed from completed.data and appended to target-file)
  < filter > move [target-file]     (matching tasks removed from pending.data and appended to target-file)
  < filter > delete                 (deletes matching tasks from completed.data)
  sort [sort-field(s)]              (sort lines in pending.data, according to task sort-field(s))
  
config options (set in script);
  
  backup_required=yes/no            (whether a date.taskdata.gz file must be present, before proceding)
  backup_frequency=N                (sets the maximum number of days between backups (0 = every time, auto)
  archive_target=~/path/file.data   (sets default archive target file)
  move_target=~/path/file.data      (sets default move target file)
  default_sort=field1-,field2+      (sets default sort order, defined like tasks report.X.sort= config)
</pre>
  
  taskdata should generate ample feedback and confirmational prompts (y/n)



