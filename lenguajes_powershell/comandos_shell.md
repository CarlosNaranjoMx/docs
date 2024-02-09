- [comandos_shell](#comandos_shell)
    - [hardcode_rename_and_move](#hardcode_rename_and_move)
    - [harcode_move](#harcode_move)
    - [move_files](#move_files)
    - [renombramiento02](#renombramiento02)
    - [replace](#replace)
    - [files](#files)
    - [az](#az)
    - [closewindows](#closewindows)

# comandos_shell


~~~powershell
~~~

## hardcode_rename_and_move
~~~powershell

function hard_rename_move {
  
  $archivos = get-childitem
  $dir_actual_nombre = Split-Path -Path . -Leaf

  foreach ($archivo in $archivos) {
    rename-item $archivo -newname ($dir_actual_nombre+"_"+($archivo.name))
  }

  $archivos = get-childitem
  foreach ($archivo in $archivos) {
    mv $archivo -destination ..
  }

  cd ..;
  remove-item $dir_actual_nombre


}

  ## renombramiento

depende del directorio actual

recibe el nombre destino
 
~~~powershell
get-location | % {$_.path}
~~~

## harcode_move

~~~powershell
function hard_move {
  $archivos = get-childitem
  foreach ($archivo in $archivos) {
    mv $archivo -destination ..
  }
}
~~~

## move_files
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

## renombramiento02
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
## replace
~~~powershell

function replace {
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
}

~~~

  ## files
  ~~~powershell
  function show-info{
      get-childitem | % { 
              if ( $_.gettype().name -eq "DirectoryInfo" ){
                  
              }else{
  
              }
      }
  }
  ~~~

  ## az
  ~~~powershell
  for ($test = 0; $test -lt 26; $test++)
  {
      new-item ([char](65 + $test)) -itemtype "directory"
  }
  ~~~

  ## closewindows
  ~~~powershell
  $a = (New-Object -comObject Shell.Application).Windows() |
   ? { $_.FullName -ne $null} |
   ? { $_.FullName.toLower().Endswith('\explorer.exe') } 
  
   $a | % {  $_.Quit() }
  ~~~
