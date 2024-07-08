# LogOffReck
Temp

# Query the most recent logoff event from the Event Log
$lastLogoffEvent = Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4634} -MaxEvents 1 | Select-Object -Property TimeCreated, @{Name='User';Expression={$_.Properties[5].Value}}

# Output the logoff event details
if ($lastLogoffEvent) {
    Write-Output "Last Logoff Event:"
    Write-Output "Time: $($lastLogoffEvent.TimeCreated)"
    Write-Output "User: $($lastLogoffEvent.User)"
} else {
    Write-Output "No logoff events found."
}
****
