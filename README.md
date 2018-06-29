# Dynamic-getter-and-setter-in-java


 ## This is the basic code to make getter and setter dynamic
````java
  DynamicDto o1;
	String variableName = "variable1";

	Object objeto = new PropertyDescriptor(variableName, DynamicDto.class).getReadMethod().invoke(o1);
```


 ## This code use  getter and setter dynamic  in a compare
````java
  @Override
  public int compare(DynamicDto o1, DynamicDto o2) {

      int salida = -1;

      Date fecha = new Date();
      try {
              Object objeto = new PropertyDescriptor(variableName, DynamicDto.class).getReadMethod().invoke(o1);
              Object objeto2 = new PropertyDescriptor(variableName, DynamicDto.class).getReadMethod().invoke(o2);

          if (("String").equalsIgnoreCase(o1.getClass().getDeclaredField(variableName).getType().getSimpleName())){
               salida = compareCamposString(objeto.toString(), objeto2.toString());
           }
           else if (("Integer").equalsIgnoreCase(o1.getClass().getDeclaredField(variableName).getType().getSimpleName())){
               salida = compareCamposInt(Integer.parseInt(objeto.toString()), Integer.parseInt(objeto2.toString())); 
           }
           else if (("BigDecimal").equalsIgnoreCase(o1.getClass().getDeclaredField(variableName).getType().getSimpleName())){
               salida = compareCamposBigDecimal(new BigDecimal(objeto.toString()), new BigDecimal(objeto2.toString()));

           }else if (("Date").equalsIgnoreCase(o1.getClass().getDeclaredField(variableName).getType().getSimpleName())){
               salida = compareCamposDate( (Date) objeto, (Date) objeto2 ); 
           }


      } catch (Exception e) {
      log.error(e.getMessage());
      }
      return salida;
  }  
````
