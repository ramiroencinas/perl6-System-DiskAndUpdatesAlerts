# System::DiskAndUpdatesAlerts

Send email alert about disk capacity and pending updates.

## Required Perl 6 modules:

- FileSystem::Capacity
- Package::Updates

## Features:

- Reports when exceed `$disk-limit-percent` at any mount point or letter drive.
- Reports if there are pending updates.
- Nice HTML table format.

## Example:
```Perl6
use v6;
use lib 'lib';
use System::DiskAndUpdatesAlerts;

my $smtp-server = 'smtp.foo.com';
my $smtp-port = 25;
my $from = 'alerts@foo.com';
my $to = 'sysadmin@foo.com';
my $disk-limit-percent = 75;

send-alerts(:$smtp-server, :$smtp-port, :$from, :$to, :$disk-limit-percent);
```

## Windows considerations

The `get-updates.ps1` Powershell script `must be located` in the same directory as the Perl6 script.

## SMTP considerations

- Sender authentication not supported.
- Encrypted transmission not supported.
- The current host and `$from` email address `must` have no restrictions to send email messages to `$smtp-port` at `$smtp-server`.
- The `$to` email address `must` exist at `$smtp-server` email server system.
