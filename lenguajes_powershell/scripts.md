
- [comandos_matriz](#comandos_matriz)
    - [compare_files_images](#compare_files_images)
    - [convert_ico](#convert_ico)
    - [copyphone](#copyphone)
- [comandos_servicios](#comandos_servicios)
    - [electronapp](#electronapp)
    - [gitliveserver](#gitliveserver)
    - [js_servidor](#js_servidor)
    - [laravel](#laravel)
    - [firefox-web](#firefox-web)
    - [links2](#links2)
    - [open](#open)
    - [php_servidor](#php_servidor)
    - [plain_text](#plain_text)
    - [slinks](#slinks)
    - [sumatra](#sumatra)
    - [translate](#translate)
    
# comandos_matriz

comentario agregado

  ## compare_files_images
  ~~~powershell
  function compare-images {
    $list = get-childitem
    $inicial 
    $siguiente
    $count = $list.Length-1
    for ($i = 0; $i -lt $count; $i++) {
    
      $inicial = $list[$i]
      $siguiente = $list[$i+1]
      if(Compare-Object -ReferenceObject $(Get-Content $inicial) -DifferenceObject $(Get-Content $siguiente)){
      }Else{ 
        remove-item $inicial
      }
      echo "$i/$count"
    }
    [console]::beep(1000,500)
  }
  ~~~
  
  ## convert_ico
  ~~~powershell
  function ConvertTo-Icon
  {
      <#
      .Synopsis
          Converts image to icons
      .Description
          Converts an image to an icon
      .Example
          ConvertTo-Icon -File .\Logo.png -OutputFile .\Favicon.ico
      #>
      [CmdletBinding()]
      param(
      # The file
      [Parameter(Mandatory=$true, Position=0,ValueFromPipelineByPropertyName=$true)]
      [Alias('Fullname')]
      [string]$File,
      
      # If set, will output bytes instead of creating a file
      [switch]$InMemory,
      
      # If provided, will output the icon to a location
      [Parameter(Position=1, ValueFromPipelineByPropertyName=$true)]
      [string]$OutputFile
      )
      
      begin {
          Add-Type -AssemblyName System.Windows.Forms, System.Drawing
      }
      
      process {
          #region Load Icon
          $resolvedFile = $ExecutionContext.SessionState.Path.GetResolvedPSPathFromPSPath($file)
          if (-not $resolvedFile) { return }
          $loadedImage = [Drawing.Image]::FromFile($resolvedFile)
          $intPtr = New-Object IntPtr
          $thumbnail = $loadedImage.GetThumbnailImage(72, 72, $null, $intPtr)
          $bitmap = New-Object Drawing.Bitmap $thumbnail 
          $bitmap.SetResolution(72, 72); 
          $icon = [System.Drawing.Icon]::FromHandle($bitmap.GetHicon());         
          #endregion Load Icon
  
          #region Save Icon
          if ($InMemory) {                        
              $memStream = New-Object IO.MemoryStream
              $icon.Save($memStream) 
              $memStream.Seek(0,0)
              $bytes = New-Object Byte[] $memStream.Length
              $memStream.Read($bytes, 0, $memStream.Length)                        
              $bytes
          } elseif ($OutputFile) {
              $resolvedOutputFile = $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath($outputFile)
              $fileStream = [IO.File]::Create("$resolvedOutputFile")                               
              $icon.Save($fileStream) 
              $fileStream.Close()               
          }
          #endregion Save Icon
  
          #region Cleanup
          $icon.Dispose()
          $bitmap.Dispose()
          #endregion Cleanup
  
      }
  }
  ~~~

## copyphone
~~~powershell
function copy-phone {
  
  <#
  .SYNOPSIS

  #>
  $Shell = New-Object -ComObject Shell.Application

  $TargetFolderShell = $Shell.NameSpace("C:\Users\cnaranjo\Pictures\Camera").self

  $ShellItem = $Shell.NameSpace(17).Self
  $Phone = $ShellItem.GetFolder.Items() | ? {$_.Name -eq "ALE-L23"}
  $Dir01 = $Phone.GetFolder.Items() | ? { $_.Name -match "Memoria Interna" }
  $Camera = $Dir01.GetFolder.Items() | ? { $_.Name -match "DCIM" }

  $Telegram = $Dir01.GetFolder.Items() | ? { $_.Name -match "Telegram" }
  $TelegramDocuments = $Telegram.GetFolder.Items() | ? { $_.Name -match "Telegram Documents" }

  $TargetFolderShell.GetFolder.CopyHere($Camera)
  $TargetFolderShell.GetFolder.MoveHere($TelegramDocuments)

  sleep(20)

}
~~~

# comandos_servicios
  ## electronapp
  ~~~powershell
  function start-electron{
    <#
      .SYNOPSIS
    #>
    start-process powershell {
      set-location 'C:\Users\cnaranjo\Desktop\pruebas-web\ELECTRON\electron-quick-start' ;
      npm start
    }
  }
  ~~~
 ## gitliveserver
  ~~~powershell
  D:
  cd live-server
  git add -A; git commit -m "save commit"; git push origin master;
  ~~~
  ## js_servidor
  ~~~powershell
  cd C:\Users\cnaranjo\Desktop\notas\live-server\live-server;
  live-server
  ~~~
  ## laravel
  ~~~powershell
  D: ;
  cd \live-server\server_laravel;
  php artisan serve;
  ;
  ~~~

## firefox-web
~~~powershell
funciton search-firefox {

<#
    .SYNOPSIS
#>

[CmdletBinding()]
param (
    [Parameter()]
    [String]
    $site,
    [String]
    $web
)
# [system.Diagnostics.Process]::Start("firefox","https://web.telegram.org/#/im?p=s1213008577_17731116373103605606")
    switch ($site) {
        "wiki" { Start-Process firefox "https://en.wiktionary.org/wiki/$web" }
        Default {}
    }
}

~~~

## links2
~~~powershell
new-item -itemtype symboliclink -path "C:\Users\cnaranjo\Programs" -target $($args[0]) -name $($args[1])
~~~

## open
~~~powershell
[CmdletBinding()]
param (
    [Parameter()]
    [String]
    $archivo
)
switch ($archivo) {
    "pharsalva" { start-process notepad "C:\Users\cnaranjo\Desktop\idiomas\ingles\pharsal-verbs\pharsal-verbs.txt" }
    Default {}
}

Get-ExecutionPolicy
Set-ExecutionPolicy AllSigned

Set-ExecutionPolicy Bypass -Scope Process -Force;
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072;
iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
~~~
## php_servidor
~~~powershell
cd C:\Users\cnaranjo\Desktop\notas\live-server\server_laravel;
php artisan serve;
;
~~~
## plain_text
~~~powershell
$ps1_files = (get-childitem | ? extension -eq .ps1)
foreach ($ps1 in $ps1_files) {
  echo "## $ps1.Name"
  echo ~~~
powershell  get-content $ps1
  echo ~~~
}
~~~

## slinks
~~~powershell
if (!([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)) {
    Start-Process PowerShell -Verb RunAs /
    "-NoProfile -ExecutionPolicy Bypass -Command `"powershell;`"";
    exit;
}
~~~
## sumatra
~~~powershell
[CmdletBinding()]
param (
    [Parameter()]
    [String]
    $file
)

# $file = 'C:\Users\cnaranjo\Desktop\05-libros\Diccionarios\diccionario.pdf'
Start-process sumatraPdf $file
~~~
## translate
~~~powershell
[system.Diagnostics.Process]::Start("firefox","https://translate.google.com/")
~~~
