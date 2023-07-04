# comandos_for 
 
  ## recorrer diccionario
  ~~~powershell
  function vars_print {
    param ()
    foreach($path in $vars.GetEnumerator()){
      echo "$($path.Name) $($path.Value)"
    }
    #end_fun
  }
  ~~~
