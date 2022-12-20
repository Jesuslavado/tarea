# tarea
 //CONSTANTES
            const int MAX_HT=60; //NUMERO MÁXIMO DE HORAS DE TRABAJO
            const int MAX = 35; // APARTIR DE ESTE VALOR LAS HORAS NORMALES PASAN A SER HORAS EXTRAS
            const float PRECIO_MAX = 22.50f; // CANTIDAD MÁXIMA QUE TE PUEDEN PAGAR POR HORA
            const float PRECIO_MIN = 1f; // CANTIDAD MINIMA QUE TE PUEDEN PAGAR POR HORA
            const int MULTIPLICACION = 16; // VALOR CREADO PARA HACER EL CALCULO DEL 16%
            const int DIVISION = 100;// VALOR CREADO PARA HACER EL CALCULO DEL 16%
            const float MULTIPLICACIO_EXTRA = 1.5F; // VALOR QUE NOS SERVIRA PARA CALCULAR CUANTO GANARA POR LAS HORAS EXTRAS
            const int MIN_HT = 1; // NUMERO MÍNIMO DE HORAS TRABAJADAS
            //VARIABLES
            string nombre, apellido1, apellido2, puesto; //PARA PODER INTRODUCIR VALORES QUE NO SON NUMERO
            int horastrabajadas, horasextra;// SEÑALIZACIÓN DE HORAS CON VALOR SIN DECIMALES
            bool esCorrecto;// IDENTIFICADOR DE ERRORES
            string aux;// NOS SERVIRA DE AUXILIAR PARA LUEGO CONVERTIR ALGUNOS VALORES
            float salariobase, salarioextra, salariobruto, impuesto, salarioneto, preciohora; //SEÑALIZACION PARA VALORES QUE PUEDEN TENER DECIMALES
            //INICIALIZACIÓN
            nombre = "";
            apellido1 = "";
            apellido2 = "";
            puesto = "";
            esCorrecto = true;
            aux = "";
            horasextra = 0;
            preciohora = 0f;
            salariobase = 0f;
            salarioextra = 0f;
            salariobruto = 0f;
            impuesto = 0f;
            salarioneto = 0f;
            //ENTRADA
            Console.WriteLine($"ESTA ES LA PRIMERA NOMINA, ESPERO QUE LE GUSTE \n"); //NOS APARECERA AL INICIAR EL PROGRAMA

            Console.WriteLine("Introduzca su puesto de trabajo: ");
             puesto = Console.ReadLine();

            Console.WriteLine("Introduzca su nombre: ");
            nombre = Console.ReadLine();

            Console.WriteLine("Introduzca su primer apellido: ");
            apellido1 = Console.ReadLine();

            Console.WriteLine("Introduzca su segundo apellido: ");
            apellido2 = Console.ReadLine();
           
            //INICIO DEL BUCLE QUE PONDRA UN MENSAJE REPETIDAMENTE MIENTRAS LAS HORAS SEAN MAYORES DE 60
            do
            {
                Console.WriteLine("Introduzca las horas trabajadas: ");
                aux = Console.ReadLine();
                esCorrecto = Int32.TryParse(aux, out horastrabajadas);

                //IF CREADO PARA QUE REPITA UN MENSAJE HASTA QUE SE ENCUENTRE ENTRE LOS VALORES CORRECTOS
                if (horastrabajadas > MAX_HT || horastrabajadas < MIN_HT)
                {
                    esCorrecto = false;
                    Console.WriteLine("El valor no puede ser superior a 60 o inferior a 1");
                }

            } while (!esCorrecto);

            //INICIO DEL BUCLE QUE PONDRA UN MENSAJE REPETIDAMENTE MIENTRAS EL PRECIO DE LA HORA SEA SUPERIOR A 22,5€
            do
            {
                Console.WriteLine("Introduzca el precio por hora: ");
                aux=Console.ReadLine();
                esCorrecto = float.TryParse(aux, out preciohora);

                //IF CREADO PARA QUE REPITA UN MENSAJE HASTA QUE SE ENCUENTRE ENTRE LOS VALORES CORRECTOS
                if (preciohora > PRECIO_MAX || preciohora < PRECIO_MIN)
                {
                    esCorrecto = false;
                    Console.WriteLine("EL valor introducido no puede ser mayor a 22,5 o inferior a 1");
                }

            }while(!esCorrecto);

            //PROCESO
            salariobase = horastrabajadas * preciohora; // CALCULO PARA HACER EL SALARIO BASE
            salariobruto = salarioextra + salariobase; // CALCULO PARA HACER EL SALARIO BRUTO
            impuesto = (salariobruto * MULTIPLICACION) / DIVISION; // CALCULO PARA REALIZAR EL IMPUESTO
            salarioneto = salariobruto - impuesto; // CALCULO PARA HACER EL SALARIO NETO

            if (horastrabajadas > MAX)// SI LAS HORAS TRABAJADAS SUPERAN EL VALOR MAX SE REALIZARA LOS SIGUIENTE
            {
                horasextra = MAX; 
                horasextra = horastrabajadas - horasextra; // APARTIR DEL VALOR MAX TODAS LAS HORAS SE RESTARAN Y SERAN HORAS EXTRAS
                salarioextra = horasextra * (preciohora * MULTIPLICACIO_EXTRA); // CALCULO PARA SABER CUANTO VALEN LAS HORAS EXTRAS
            }
            //SALIDA 
            // EL PROGRAMA QUE SE VERA DE LA SIGUIENTE MANERA SI TODO A FUNCIONADO CORRECTAMENTE:
            Console.WriteLine($"\n \nPuesto:     {puesto}");
            Console.Write($"Nombre:     {nombre}");
            Console.Write($"   Apellidos:     {apellido1}");
            Console.WriteLine($" {apellido2}");
            Console.WriteLine("***********************************************************************************************************************");
            Console.Write($"Horas trabajadas: {horastrabajadas} Horas  ");
            Console.WriteLine($"Horas Extras:     {horasextra} Horas");
            Console.WriteLine($"Precio por Hora:     {preciohora} Euros/hora");
            Console.WriteLine("***********************************************************************************************************************");
            Console.Write($"Salario base:    {salariobase} Euros");
            Console.WriteLine($"     Salario extra:    {salarioextra} Euros");
            Console.WriteLine("***********************************************************************************************************************");
            Console.WriteLine($"Salario Bruto:     {salariobruto} Euros");
            Console.WriteLine($"Impuestos:          {impuesto} Euros");
            Console.WriteLine($"Salario Neto:      {salarioneto} Euros");
           
