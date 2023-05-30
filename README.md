# Minha-evolu-o-em-programa-o-de-programacao---C
Neste codigo eu utilizo de funções, matrizes bidimensionais e unidimensionais e a logica para gerar numeros aleatorios e alocá-los na matriz de 40 linhas e 5 colunas e depois envio esta matriz como parametro para uma função realizar a verificação a  cada valor, os que forem primos, vão para um vetor e serão apresentados na tela ao final.

#include<stdio.h>
#include<stdlib.h>

void funcao_maior_menor(int vetorplus[200], int quantidadedeprimos){
    int maior,menor,soma;
    
    maior = menor = vetorplus[0];
    
    for(int i = 0; i< 200; i++){
        if(vetorplus[i] > maior)maior = vetorplus[i];
        else if(vetorplus[i] < menor && vetorplus[i] != 0)menor = vetorplus[i];
        
        soma += vetorplus[i];   
    }
    float media = soma / quantidadedeprimos;
    printf("\no maior primo no vetor de numeros primos sorteados foi %d e o menor foi %d e a media foi %.2f ,  a quantidade de primos foi %d",maior, menor, media,quantidadedeprimos);
    
}

void funcaoverificacao(int matrizpri[40][5]){
    int ver,i,j,contador,vetorprimos[200],i2=0;
    int cont;
    
    for(i = 0; i < 200; i++){
        vetorprimos[i] = 0; 
    }

    for(i=0;i<40;i++){
        for(j=0;j<5;j++){
            contador = matrizpri[i][j];
            while(contador > 0){
                if(matrizpri[i][j]%contador==0){ // sempre que for divisivel por valores abaixo dele, a variavel de verificacao vai receber + 1
                    ver++;
                }
                contador--;
            }
            
            if(ver==2){ //verificando se o valor é primo, pois um numero primo so é divisivel por 1 e por ele mesmo
                vetorprimos[i2] = matrizpri[i][j];
                i2++;
            }
            ver = 0;
        }
    }
    for(i =0; i < 200; i++ ){
        if(vetorprimos[i] != 0){
            printf(" [%d] \t",vetorprimos[i]);
            if(i %5==0)printf("\n");
            cont++;
        }
        
        
    }
    funcao_maior_menor(vetorprimos,cont); // enviando o vetor preenchido apenas com os numeros primos que foram sorteados inicialmente na funcao main
       
}

int main(){
    int i,j,matriz[40][5];
    
    for(i=0;i<40;i++){
        for(j=0;j<5;j++){
            matriz[i][j] = rand()%200;
        }
    }
    
    funcaoverificacao(matriz); // enviando a matriz bidimensional ja preenchida para a funcao
    
}

