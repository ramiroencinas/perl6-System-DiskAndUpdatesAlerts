# System::DiskAndUpdatesAlerts

Send email alerts about disk capacity and pending updates.

## Required Perl 6 modules:

- FileSystem::Capacity
- Package::Updates

## Features:

- Reports when exceed the set percentage of capacity at any mount point or letter drive.
- Reports if there are pending updates.
- Nice HTML table format.

## Example:
```Perl6
use v6;
use lib 'lib';
use System::DiskAndUpdatesAlerts;

my $smtp-server = 'smtp.foo.com';
my $smtp-port = 25;
my $from = 'foo@bar.com';
my $to = 'bar@foo.com';
my $disk-limit-percent = 75;

send-alerts(:$smtp-server, :$smtp-port, :$from, :$to, :$disk-limit-percent);
```

## Windows considerations

The `get-updates.ps1` Powershell script `must be located` in the same directory as the Perl6 script.
