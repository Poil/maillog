Maillog a Postfix log analyzer
==================================

Introduction.
---------

When a mail server processes an email, he writes to the log file a few lines. In large mail traffic belonging to different rows are shuffled letters, sometimes records relating to the same letter are spaced apart by several tens of rows. This greatly hinders the reading log. To solve this problem, in the old days, I wrote a script in Perl original name maillog. Over time, it added functionality, bug fixes. And now if you have any questions by e-mail, the first thing we do is run this script.


 Capabilities.
------------

The script scans the log files that includes lines of letters. Entries are highlighted in color depending on the success of the delivery addresses are highlighted.

It is possible to filter messages by sender and / or the sender, the -f and -t, respectively.

By using the -d option, you can specify a date or range of dates for which to display the letter. Dates can be set in different ways, for example:

12.1.2010-15.1.2010 - show the letter from the 12th to the 15th inclusive. 10.01.2010- - letters passed from the 10th and later. -12.01 - Contrary to the previous embodiment, the 12th and earlier. If it omitted the year or month, then the current substitutes. - - In general, all that was 1.1.2010 - for the 1st January 2010. By default, it displays the letter for today.

If you want to see only messages with errors, ie, have not been delivered, you can use -e option.

All of these keys can be used in any combination.

There is support for log files, compressed after the rotation. 

 Setting.
----------

Settings are not many :)
At the beginning of the script is a string "my $ filePattern = '/var/log/mail/mail*.log';" it is given the name of the template for the mail server logs.


 Limitations.
------------

The logs are written to only date and month, so it is impossible to filter emails by year. You can always omit the year in the -d option. If anyone has ideas, please contact me.

I have a month in the log is written in English Jan, Feb, etc., if someone they are Russian, Russian add elements to hash% MONTHS.

The script works only with logs postfix. I do not remember much different from other server logs may actually add support of other programs. 

Using (help).
--------------

    maillog [-d DATE] [-f FROM] [-t TO] [-e] [-h] [-V]

    Displays entries in the mail log for messages coming from the FROM address to the TO address for the period indicated in the DATE option.

        -f  FROM    e-mail address of the sender (or a portion thereof).

        -t  TO      e-mail address of the recipient (or a portion thereof).

        -d  DATE    output report for the period, if the option is omitted entries are displayed only for the current day.

            DD/MM/YY-DD/MM/YY   full format :

            -DD/MM/YY           Expected starting date:
                                They will be shown records with January 1, 1970

            DD/MM/YY-           Expected end date:
                                records are displayed to the current date.

            -                   Expected a start and end dates:
                                Entries will be displayed from 1 January 1970 to
                                current date.

        -e          Show the undelivered messages.

        -h          Show help page.

        -V          Show version and license.


License GPLv2.
---------------
This program is free software; you can redistribute it and/or modify t under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2, or (at your option) any later version.
