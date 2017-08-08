# System::DiskAndUpdatesAlerts

[![Build Status](https://travis-ci.org/ramiroencinas/perl6-System-DiskAndUpdatesAlerts.svg?branch=master)](https://travis-ci.org/ramiroencinas/perl6-System-DiskAndUpdatesAlerts)

Send email alert about disk capacity and pending updates.

## Required Perl 6 modules:

- FileSystem::Capacity
- Package::Updates

## Features:

- Reports when exceed `$disk-limit-percent` capacity at any mount point or letter drive.
- Reports the pending updates from popular GNU/Linux package managers or Windows Update.
- Nice HTML table format.

## Example:
```Perl6
use v6;
use System::DiskAndUpdatesAlerts;

my $smtp-server = 'smtp.foo.com'; # Target email server
my $smtp-port = 25; # SMTP port from target email server
my $from = 'alerts@foo.com'; # Whatever but descriptive
my $to = 'sysadmin@foo.com'; # The receiver of alerts
my $disk-limit-percent = 75; # Reaching this percent reports the disk alert

send-alerts(:$smtp-server, :$smtp-port, :$from, :$to, :$disk-limit-percent);
```

## Windows considerations

The `get-updates.ps1` Powershell script must be located in the same directory as the Perl6 script.

## SMTP considerations

- Sender authentication is not supported.
- Encrypted transmission is not supported.
- The current hostname and `$from` email address must have no restrictions to send email messages to `$smtp-port` at `$smtp-server`.
- The `$to` email address must exist at `$smtp-server` email server system.
