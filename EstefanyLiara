#include <stdio.h>
#include <string.h>

#define MAX_CARTAS 10

typedef struct {
    char estado[50];
    int codigo;
    char nome[50];
    int populacao;
    double pib;
    double area;
    int pontos_turisticos;
} Carta;

double calcularDensidade(Carta c) {
    return c.area > 0 ? c.populacao / c.area : 0;
}

double calcularPibPerCapita(Carta c) {
    return c.populacao > 0 ? (c.pib * 1e9) / c.populacao : 0;
}

void exibirCarta(Carta c, int indice) {
    printf("\n--- Carta %d ---\n", indice + 1);
    printf("Estado: %s\n", c.estado);
    printf("Codigo: %d\n", c.codigo);
    printf("Cidade: %s\n", c.nome);
    printf("Populacao: %d\n", c.populacao);
    printf("PIB: %.2f bilhoes\n", c.pib);
    printf("Area: %.2f km2\n", c.area);
    printf("Pontos turisticos: %d\n", c.pontos_turisticos);
    printf("Densidade populacional: %.2f hab/km2\n", calcularDensidade(c));
    printf("PIB per capita: %.2f\n", calcularPibPerCapita(c));
}

void compararCartas(Carta c1, Carta c2, int atributo) {
    double valor1, valor2;
    printf("\nComparacao entre %s e %s:\n", c1.nome, c2.nome);
    switch (atributo) {
        case 1: 
            valor1 = c1.populacao; valor2 = c2.populacao;
            printf("Populacao: %d vs %d\n", c1.populacao, c2.populacao);
            break;
        case 2: 
            valor1 = c1.pib; valor2 = c2.pib;
            printf("PIB: %.2f vs %.2f bilhoes\n", c1.pib, c2.pib);
            break;
        case 3: 
            valor1 = c1.area; valor2 = c2.area;
            printf("Area: %.2f vs %.2f km2\n", c1.area, c2.area);
            break;
        case 4: 
            valor1 = c1.pontos_turisticos; valor2 = c2.pontos_turisticos;
            printf("Pontos turisticos: %d vs %d\n", c1.pontos_turisticos, c2.pontos_turisticos);
            break;
        case 5: 
            valor1 = calcularDensidade(c1); valor2 = calcularDensidade(c2);
            printf("Densidade populacional: %.2f vs %.2f hab/km2\n", valor1, valor2);
            break;
        case 6: 
            valor1 = calcularPibPerCapita(c1); valor2 = calcularPibPerCapita(c2);
            printf("PIB per capita: %.2f vs %.2f\n", valor1, valor2);
            break;
        default: 
            printf("Atributo invalido!\n");
            return;
    }
    
    if (valor1 > valor2) {
        printf("\nVencedor: %s\n", c1.nome);
    } else if (valor2 > valor1) {
        printf("\nVencedor: %s\n", c2.nome);
    } else {
        printf("\nEmpate!\n");
    }
}

int main() {
    Carta cartas[MAX_CARTAS];
    int num_cartas = 0, opcao, atributo, c1, c2;

    printf("========================================="
           "\n  Bem-vindo ao Super Trunfo Novato!\n"
           "=========================================");

    do {
        printf("\n--- Menu ---\n");
        printf("1. Adicionar carta\n");
        printf("2. Exibir cartas\n");
        printf("3. Comparar cartas\n");
        printf("0. Sair\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);
        getchar(); // Limpa buffer

        switch (opcao) {
            case 1:
                if (num_cartas < MAX_CARTAS) {
                    printf("Estado: ");
                    fgets(cartas[num_cartas].estado, 50, stdin);
                    strtok(cartas[num_cartas].estado, "\n");
        
                    printf("Codigo: ");
                    scanf("%d", &cartas[num_cartas].codigo);
        
                    printf("Nome da cidade: ");
                    getchar();  // Limpa o buffer antes de ler a string do nome da cidade
                    fgets(cartas[num_cartas].nome, 50, stdin);
                    strtok(cartas[num_cartas].nome, "\n");
        
                    printf("Populacao: ");
                    scanf("%d", &cartas[num_cartas].populacao);
        
                    printf("PIB (em bilhoes): ");
                    scanf("%lf", &cartas[num_cartas].pib);
        
                    printf("Area (km2): ");
                    scanf("%lf", &cartas[num_cartas].area);
        
                    printf("Pontos turisticos: ");
                    scanf("%d", &cartas[num_cartas].pontos_turisticos);
        
                    num_cartas++;
                    printf("\nCarta adicionada com sucesso!\n");
                } else {
                    printf("Limite de cartas atingido!\n");
                }
                break;

            case 2:
                if (num_cartas == 0) {
                    printf("\nNenhuma carta cadastrada ainda!\n");
                } else {
                    for (int i = 0; i < num_cartas; i++) {
                        exibirCarta(cartas[i], i);
                    }
                }
                break;

            case 3:
                if (num_cartas < 2) {
                    printf("\nCadastre pelo menos duas cartas antes de comparar!\n");
                    break;
                }
                printf("\nEscolha as cartas para comparar (0 a %d): ", num_cartas - 1);
                scanf("%d %d", &c1, &c2);
                
                if (c1 < 0 || c1 >= num_cartas || c2 < 0 || c2 >= num_cartas || c1 == c2) {
                    printf("Cartas invalidas!\n");
                    break;
                }

                printf("\nEscolha o atributo para comparacao:\n");
                printf("1. Populacao\n2. PIB\n3. Area\n4. Pontos turisticos\n5. Densidade populacional\n6. PIB per capita\n");
                scanf("%d", &atributo);

                compararCartas(cartas[c1], cartas[c2], atributo);
                break;

            case 0:
                printf("\nObrigado por jogar! Ate a proxima!\n");
                break;

            default:
                printf("Opcao invalida! Tente novamente.\n");
        }
    } while (opcao != 0);

    return 0;
}
