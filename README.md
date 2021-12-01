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

ULTIMA PARTE 

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <stdbool.h>

enum opciones{ JUGAR = 1, REGLAS, SALIR};
void menu(); 
void printMatrizmin(int arr[9][9], int n);//imprimir la matriz
struct cords {
    int x;
    int y;
};
int par(int arr[9][9], struct cords, struct cords); //saber si la pareja es valida
int parvalido(struct cords, struct cords); //los puntos que da dicha pareja


struct cords fillcords(); //funcion para ingresar las cordenadas de los puntos que uno quiere emparejar

int end(int arr[9][9], int o);
void sumarpuntaje(int *, struct cords, struct cords);
void sumarfilas(int *);

int main(int argc, char const *argv[]) 

{	
	int puntaje = 0;
	int *pospuntaje = &puntaje;

	int filas = 9;
	int *punterofilas = &filas;
	

	int matriz[9][9];
	
	srand(time(NULL));

	
	for (int i = 0; i < 9; ++i)
	{
		for (int j = 0; j < 9; ++j)
		{
			matriz[i][j]=1+rand()%9;

		}
	}
	//creacion de matriz aleatoria


	enum opciones opcion;
	
	do{
        menu();
        printf("Seleccione una opcion: ");
        scanf("%d",&opcion);
		printf("\n");
        
        if (opcion == 3){
            break;
        }

       
        
        switch (opcion) {
            case JUGAR:
				do{
				

				struct cords n1, n2;	
				printMatrizmin(matriz, filas);
				printf ("\npuntaje: %d", puntaje);
				printf ("\nElija las posicion 1\n");

				n1 = fillcords();
				printf ("\nElija las posicion 2\n");
				n2 = fillcords();

				if (par(matriz, n1, n2) == 1){
					
					if (parvalido(n1, n2) != 0){
						sumarpuntaje(pospuntaje, n1, n2);
						matriz[n1.x][n1.y] = 0;
						matriz[n2.x][n2.y] = 0;
					} else {printf ("\nElija una pareja valida\n");}


				}

				
				if (end(matriz, filas) == 0){
					sumarfilas(punterofilas);
				}
								
				}while(puntaje < 20);
				
                
            case REGLAS:
                printf("Las reglas de Match 10 son simples: \n");
				printf("junte las parejas de tejas para conseguir 10 en total o dos numeros iguales.\n");
				printf("Las parejas deben estar a la par ya sea de manera vertical, horizontal o diagonas.\n");
				printf("Es posible hacer una pareja de un numero que se encuentre al final de una fila y otro que se encuentre al inicio de la siguiente fila\n");
				printf("El juego termina al conseguir un muntaje de 20 \n");
                break;

            
            
        }
    } while (opcion != 4);

	
	return 0;
}

void menu() {
    printf("\n1.JUGAR\n2.REGLAS\n3.SALIR\n");
}



void printMatrizmin(int arr[9][9], int n){
	
	
	for (int i = 0; i < n; ++i){
		
		for (int j = 0; j < 9; ++j){
			
			if (j % 2 == 0){
				if (arr[i][j] == 0){
					printf("   ");
				}else{printf(" %d ", arr[i][j] );}

			} else {
				if (arr[i][j] == 0) {printf("|   |");
				}else{printf("| %d |", arr[i][j] );}}
			
		}
		
												
		if (i != n-1) {printf ("\n-----------------------------------\n");}	
	}

}

int par(int arr[9][9], struct cords n1, struct cords n2){
	if 	(arr[n1.x][n1.y] != 0){
		if ((arr[n1.x][n1.y] == arr[n2.x][n2.y]) || (arr[n1.x][n1.y] + arr[n2.x][n2.y] == 10)) // funcion para saber si la pareja es valida
		return 1;
		else return 0;}else return 0;

}
struct cords fillcords(){
    struct  cords newcords;
    printf ("ingrese las cordenadas del 1 al 9\n");
    printf ("\nFila en X: ");
    scanf ("%d", &newcords.x);
	newcords.x = newcords.x - 1; // funcion para pedir las cordenadas
    printf ("\nColumna en Y: ");
    scanf ("%d", &newcords.y);
	printf("\n");
	newcords.y = newcords.y - 1;
    return newcords;
}

void sumarpuntaje(int *ptrpuntaje, struct cords n1, struct cords n2){ //funcion para sumar puntajes
	*ptrpuntaje = *ptrpuntaje + parvalido(n1, n2);

}


int parvalido(struct cords n1, struct cords n2){
	int par = 1;
	int fl = 2;
	int cv = 4;
	int inv = 0;


	
		if ((n1.x == n2.x && n1.y == n2.y+1) || (n1.x == n2.x && n1.y == n2.y-1)) //a la par
		return par;
		else if ((n1.x == n2.x+1 && n1.y == n2.y) || (n1.x == n2.x-1 && n1.y == n2.y)) // a la par
		return par;
		else if ((n1.x == n2.x+1 && n1.y == n2.y+1) || (n1.x == n2.x-1 && n1.y == n2.y-1)) //diagonal
		return par;
		else if ((n1.x == n2.x-1 && n1.y == n2.y+1) || (n1.x == n2.x+1 && n1.y == n2.y-1))//diagonal
		return par;
		else if (((n1.y ==  n2.y + 8) && (n1.x+1 == n2.x)) || ((n1.y == n2.y - 8) && (n1.x == n2.x+1))) //fin de una fila e inicio de otra
		return fl;		
		else if (((n1.y ==  n2.y + 8) && (n1.x-1 == n2.x)) || ((n1.y == n2.y - 8) && (n1.x == n2.x-1))) //fin de una fila e inicio de otra
		return fl;
		else return inv;


}

int end(int arr[9][9], int o){

	int a = 0;

	for (int i = 0; i < o; ++i)
	{

		for (int j = 0; j < 9; ++j)
		{
			if (arr[i][j] != 0 && i < o){{
				if ((arr[i][j] + arr[i][j+1]) == 10){
				a = a + 1;
				}else if ((arr[i][j] + arr[i][j-1]) == 10){	
				a = a + 1;
				}else if ((arr[i][j] + arr[i+1][j]) == 10){
				a = a + 1;
				}else if ((arr[i][j] + arr[i-1][j]) == 10){
				a = a + 1;
				}else if ((arr[i][j] + arr[i+1][j+1]) == 10){
				a = a + 1;
				}else if ((arr[i][j] + arr[i-1][j-1]) == 10){
				a = a + 1;	
				}else if ((arr[i][j] + arr[i+1][j-1]) == 10){
				a = a + 1;
				}else if ((arr[i][j] + arr[i-1][j+1]) == 10){
				a = a + 1;
				}else if (arr[i][j] == arr[i][j+1]){
				a = a + 1;
				}else if (arr[i][j] == arr[i][j-1]){	
				a = a + 1;
				}else if (arr[i][j] == arr[i+1][j]){
				a = a + 1;
				}else if (arr[i][j] == arr[i-1][j]){
				a = a + 1;
				}else if (arr[i][j] == arr[i+1][j+1]){
				a = a + 1;
				}else if (arr[i][j] == arr[i-1][j-1]){
				a = a + 1;	
				}else if (arr[i][j] == arr[i+1][j-1]){
				a = a + 1;
				}else if (arr[i][j] == arr[i-1][j+1]){
				a = a + 1;
				}else {a = a + 0;} 
			}}else if (arr[i][j] != 0){{
				if ((arr[i][j] + arr[i][j+1]) == 10){
				a = a + 1;
				}else if ((arr[i][j] + arr[i][j-1]) == 10){	
				a = a + 1;
				}else  if ((arr[i][j] + arr[i-1][j]) == 10){
				a = a + 1;
				}else  if ((arr[i][j] + arr[i-1][j-1]) == 10){
				a = a + 1;	
				}else  if ((arr[i][j] + arr[i-1][j+1]) == 10){
				a = a + 1;
				}else if (arr[i][j] == arr[i][j+1]){
				a = a + 1;
				}else if (arr[i][j] == arr[i][j-1]){	
				a = a + 1;
				}else  if (arr[i][j] == arr[i-1][j]){
				a = a + 1;
				}else  if (arr[i][j] == arr[i-1][j-1]){
				a = a + 1;	
				}else  if (arr[i][j] == arr[i-1][j+1]){
				a = a + 1;}
				else a = a + 0;

			}}else a = a + 0;


		}
		
	}
	return a;
	
}

void sumarfilas(int *filass){

	*filass = *filass + 1;

}
