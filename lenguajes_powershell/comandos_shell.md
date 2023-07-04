

# comandos_shell

  ## renombramiento.ps1.Name

depende del directorio actual

recibe el nombre destino
 
~~~powershell
get-location | % {$_.path}
~~~

## move_files.ps1.Name
~~~powershell
$lista = get-childitem -recurse
foreach ($item in $lista) {
  cd $item;
  $lista02 = get-childitem -recurse;
  foreach ($item02 in $lista02) {
    mv $item02 -destination ..
  }
  cd ..;
}
~~~

## renombramiento02.ps1.Name
~~~powershell
function act_newname {
  param(
    [String]
    $nombre_nuevo
  )

  $list = get-childitem 
  foreach ($l in $list) {
    rename-item $l -newname ($nombre_nuevo+"_"+($l.name))
  }
}
~~~
## replace.ps1.Name
~~~powershell
param(
  [String]
  $nombre,
  [String]
  $nombre2
)

$list = get-childitem 
foreach ($l in $list) {
  rename-item $l -newname (($l.name).replace($nombre,$nombre2))
}
~~~

  ## files.ps1.Name
  ~~~powershell
  function show-info{
      get-childitem | % { 
              if ( $_.gettype().name -eq "DirectoryInfo" ){
                  
              }else{
  
              }
      }
  }
  ~~~

  ## az.ps1.Name
  ~~~powershell
  for ($test = 0; $test -lt 26; $test++)
  {
      new-item ([char](65 + $test)) -itemtype "directory"
  }
  ~~~

  ## closewindows.ps1.Name
  ~~~powershell
  $a = (New-Object -comObject Shell.Application).Windows() |
   ? { $_.FullName -ne $null} |
   ? { $_.FullName.toLower().Endswith('\explorer.exe') } 
  
   $a | % {  $_.Quit() }
  ~~~