# mysql_bot_stats_system
Stats System for MySQL Bot Core

This is a module for MySQL Bot Core system.
You'll need https://github.com/thistehneisen/mysql_bot_core in case for this to work.

* Please note that this is in BETA version.

```
[13:47] <Neisen> !stats
[13:47] -#DEV-SQL- [Neisen:] lines: 29 words: 31 symbols: 153 joins: 2 parts: 2 actions: 0 notices: 0 // statistics calculated since 2011-09-06 13:38:48
[13:48] <Neisen> !chanstats
[13:48] -#DEV-SQL- [###:] lines: 30 words: 32 symbols: 159 joins: 2 parts: 2 actions: 0 notices: 0 // statistics calculated since 2011-09-06 13:38:48
[13:48] <Neisen> !stats hawkee
[13:48] -#DEV-SQL- [hawkee:] no stats retrieved yet.
[13:48] <Neisen> !chanstats #hawkee
[13:48] -#DEV-SQL- [#hawkee:] no stats retrieved yet.
```

MySQL Database Structure:
```
CREATE TABLE `stats` (
  `target` varchar(50) NOT NULL,
  `lines` int(10) unsigned NOT NULL DEFAULT '0',
  `words` int(10) unsigned NOT NULL DEFAULT '0',
  `symbols` int(10) unsigned NOT NULL DEFAULT '0',
  `joins` int(10) unsigned NOT NULL DEFAULT '0',
  `parts` int(10) unsigned NOT NULL DEFAULT '0',
  `actions` int(10) unsigned NOT NULL DEFAULT '0',
  `notices` int(10) unsigned NOT NULL DEFAULT '0',
  `start` datetime NOT NULL,
  PRIMARY KEY (`target`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

NOTE: The frequency of syncing is defined by the MySQL Bot Core timer, which executes m.sync. If channel(-s) has big traffic and bot starts to freeze for seconds, make the m.sync with bigger delay.
