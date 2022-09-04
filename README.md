# Pic 16F887 Memoria EEPROM

<img src="https://github.com/IDiegoUlises/Pic-EEPROM/blob/main/Images/16f887-Pic.png"  />

* **El Pic 16F887 tiene una memoria EEPROM de 256 de bytes**
* Significa que tiene 256 celdas de memoria y cada una tiene una duraccion de 100.000 veces de escritura
* Se pueden guardar datos de 0 a 255 en cada una de sus celdas
* Vdd: Positivo del microcontrolador
* Vss: Negativo del microcontrolador
* Clkin: Osicilador conectado a negativo
* Clkout: Osicilador conectado a negativo

### Codigo
```c
#include <16f887.h> //Nombre del microcontrolador
#fuses xt,nowdt  //para osciladores de 4 MegaHertz se usa xt para mayores usa hs
#use delay(clock=4M) //Velocidad del oscilador, la "M" signfica mega

void main()
{
   
   while(true)
      {
         int direccion = 255; //Selecciona la direccion de memoria
         int lectura = read_eeprom(direccion); //Realiza una lectura en la memoria EEPROM
   
         if(lectura == 1) //Si el dato almacenado es uno
         {
            output_high(pin_c0); //Enciende el led
         }
   
         else if(lectura == 0) //Si el dato almacenado es cero
         {
            output_low(pin_c0); //Apaga el led
         }
   
         if(input(pin_a0) == 1) //Realiza una lectura del boton
         {
            boolean valor = !lectura; //Cambia al estado contrario
            write_eeprom(direccion,valor); //Escribe en la EEPROM
            delay_ms(1000); //Retarado de 1 segundo
         }   
     }  
}
```

### Compilar en Css Compiler
<img src="https://github.com/IDiegoUlises/Pic-EEPROM/blob/main/Images/Codigo-Imagen.png"  />

### Conectar el Pic al Pickit 
<img src="https://github.com/IDiegoUlises/Pic-EEPROM/blob/main/Images/Pickit3.jpg" width="1000" height="500" />

### Subir el archivo Hex al Pickit 
<img src="https://github.com/IDiegoUlises/Pic-EEPROM/blob/main/Images/Importar-Hex.png"  />

### Luego subir el programa al microcontrolador con "Write"
<img src="https://github.com/IDiegoUlises/Pic-EEPROM/blob/main/Images/Write-pickit.png"  />

### Conexion
<img src="https://github.com/IDiegoUlises/Pic-EEPROM/blob/main/Images/Circuito-En-Fritizing.png" />

### Funcionamiento
![](https://github.com/IDiegoUlises/Pic-EEPROM/blob/main/Images/EEPROM.gif)
