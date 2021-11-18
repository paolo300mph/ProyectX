# ProyectX
Tarea de la U
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

enum opciones{ JUGAR, REGLAS, SALIR};
void menu();
void printMatriz(int arr[9][9]);

int main(int argc, char const *argv[])
{	
	enum opciones opcion;
	
	do{
        menu();
        printf("Seleccione una opcion: ");
        scanf("%d",&opcion);
        
        if (opcion == 3){
            break;
        }

       
        
        switch (opcion) {
            case JUGAR:
				
                break;
            case REGLAS:
                printf("Las reglas de Match 10 son simples");
				printf("– junte las parejas de tejas para conseguir 10 en total. El número que haga será su puntuación. Haga girar el campo de juego para mezclar las tejas.");
				printf("Por ejemplo: 7+3=10 (73 puntos), 4+0+2+1+3=10 (40213 puntos)");
                break;
            
            
        }
    } while (opcion != 4);

	int matriz[9][9];
	int resultado=0;
	srand(time(NULL));


	
	for (int i = 0; i < 9; ++i)
	{
		for (int j = 0; j < 9; ++j)
		{
			matriz[i][j]=1+rand()%9;

		}
	}

	printMatriz(matriz);





	return 0;
}

void menu() {
    printf("\n1.JUGAR\n2.REGLAS\n3.SALIR\n");
}

void printMatriz(int arr[9][9]){
	for (int i = 0; i < 9; ++i)
	{

		for (int j = 0; j < 9; ++j)
		{
			printf("%d ", arr[i][j]);
		}
		printf("\n");
	}

}


//MODIFICANDO EL CODIGO PARA ELIMINAR Y LLENAR CASILLAS

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

enum opciones{ JUGAR = 1, REGLAS, SALIR};
void menu();
void printMatriz(int arr[9][9]);
void printMatrizmin(int arr[9][9]);

int main(int argc, char const *argv[])
{	

	int matriz[9][9];
	
	srand(time(NULL));
	
	for (int i = 0; i < 9; ++i)
	{
		for (int j = 0; j < 9; ++j)
		{
			matriz[i][j]=1+rand()%9;

		}
	}



	enum opciones opcion;
	
	do{
        menu();
        printf("Seleccione una opcion: ");
        scanf("%d",&opcion);
        
        if (opcion == 3){
            break;
        }

       
        
        switch (opcion) {
            case JUGAR:
				printMatrizmin(matriz);
                break;
            case REGLAS:
                printf("Las reglas de Match 10 son simples: \n");
				printf("– junte las parejas de tejas para conseguir 10 en total. El número que haga será su puntuación. Haga girar el campo de juego para mezclar las tejas.\n");
				printf("Por ejemplo: 7+3=10 (73 puntos), 4+0+2+1+3=10 (40213 puntos)");
                break;
            
            
        }
    } while (opcion != 4);

	


	
	

	





	return 0;
}

void menu() {
    printf("\n1.JUGAR\n2.REGLAS\n3.SALIR\n");
}

void printMatriz(int arr[9][9]){
	for (int i = 0; i < 9; ++i)
	{

		for (int j = 0; j < 9; ++j)
		{
			printf("%d ", arr[i][j]);
		}
		printf("\n");
	}

}

void printMatrizmin(int arr[9][9]){
	for (int i = 0; i < 3; ++i){
	

		for (int j = 0; j < 9; ++j){
		
			if (j % 2 == 0){
			printf(" %d ", arr[i][j]);
			} else {printf("| %d |", arr[i][j]);}}

		if (i != 2) {printf ("\n-----------------------------------\n");}	
	}

}
