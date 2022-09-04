# Pic 16F887 Memoria EEPROM

* **El Pic 16F887 tiene una memoria EEPROM de 256 de bytes**
* Significa 256 celdas de memoria y cada una tiene una duraccion de 100.000 veces de escritura
* Se pueden guardar datos de 0 a 255 en cada una de sus celdas
* Vdd: Positivo del microcontrolador
* Vss: Negativo del microcontrolador
* Clkin: Osicilador conectado a negativo
* Clkout: Osicilador conectado a negativo

```c
#include <16f887.h> //Nombre del microcontrolador
#fuses xt,nowdt  //para osciladores de 4 MegaHertz se usa xt para mayores usa hs
#use delay(clock=4M) //Velocidad del oscilador, la "M" signfica mega

void main()
{
  
   while(true)
   {
    int direccion = 255;
    int lectura = read_eeprom(direccion);
   
   if(lectura == 1)
   {
      output_high(pin_c0); //Enciende el led
   }
   
   else if(lectura == 0)
   {
      output_low(pin_c0); //Apaga el led
   }
   
    if(input(pin_a0) == 1) //Hace una lectura
     {
         boolean valor = !lectura;
         write_eeprom(direccion,valor);
         delay_ms(1000);
     }
      
   }  
}
```
