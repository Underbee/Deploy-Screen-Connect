<# Install Automate#>
$DownloadPath = "https://screenconnect.aidepc.ca:4443/Bin/One-Sky.ClientSetup.exe?h=screenconnect.aidepc.ca&p=8041&k=BgIAAACkAABSU0ExAAgAAAEAAQDVaolrsK5KPjWzlyXPqf2Tgu54EBdrxl5sr55VJawQru7JFBNcp1ZwyDia2xnaBRsUimo%2BQ3O78dLnqa94ADRnD1hUr%2FBkUaKUd9%2ByU0ZwIqnS8je%2Br7YEia9MdWrPyukD3wM5zy7D67%2BTH8a%2Bi%2BUyVtR2DQaWGGoIg9bnlR6r2gvGUElchkHx7VCKgjnys8CvTmmrfrcYOTFxGtnfmIb11x800zxWeotLMcpH9Mpo5l17GbqVAjyovs%2FusQyvYyTYyXjleFeIymOooos%2B8q4VYe2XyVs%2F9xWUA48dQAn1LqZ5C%2BNGX%2BT4vC3CNSw7BUGw%2FHHrudTMSiMZzySFK%2Fa5&e=Access&y=Guest&t=&c=Catsports&c=&c=&c=&c=&c=&c=&c="
$SoftwarePath = "C:\Temp\One-SkySCClient.exe"

    Write-Host "Downloading from: $($DownloadPath)"
    Write-Host "Downloading to:   $($SoftwarePath)"
        $WebClient = New-Object System.Net.WebClient
        $WebClient.DownloadFile($DownloadPath, $SoftwarePath)
    Write-Host "Download Complete"

$InstallExitCode = (Start-Process -FilePath $SoftwarePath -ArgumentList " /s /CopyLogs %windir%\temp\Win10Update.log" -Wait -Verb RunAs -PassThru)
If ($InstallExitCode -eq 0) {
    If (!$Silent) {Write-Verbose "The ScreenConnect Installer Executed Without Errors"}
} Else {
    Write-Host "ScreenConnect Exit Code: $InstallExitCode" -ForegroundColor Red
    Write-Host "ScreenConnect Logs: $LogFullPath" -ForegroundColor Red
    Write-Host "The Windows 20H2 failed. Waiting 15 Seconds..." -ForegroundColor Red
    $Date = (get-date -UFormat %Y-%m-%d_%H-%M-%S)
    $LogFullPath = "$env:windir\Temp\Screenconnect_Agent_$Date.log"
}# End Else
