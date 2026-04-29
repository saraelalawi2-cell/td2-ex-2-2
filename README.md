#include <stdio.h>

/* Fonction qui calcule le MiniMax d'une matrice
   MiniMax = minimum des maximums de chaque ligne */
int MiniMax(int mat[][100], int n, int m) {
    int i, j;

   /* Variable pour stocker le MiniMax final */
    int minimax;

   /* Étape 1 : calcul du maximum de la première ligne */
    int max_ligne = mat[0][0];

  for(j = 1; j < m; j++) {
        if(mat[0][j] > max_ligne) {
            max_ligne = mat[0][j];
        }
    }

   /* On initialise le minimax avec le max de la première ligne */
    minimax = max_ligne;

   /* Étape 2 : parcourir les autres lignes */
    for(i = 1; i < n; i++) 
        /* Trouver le maximum de la ligne i */
        max_ligne = mat[i][0];

  for(j = 1; j < m; j++) {
            if(mat[i][j] > max_ligne) {
                max_ligne = mat[i][j];
            }
        }

  /* Étape 3 : garder le minimum des maximums */
        if(max_ligne < minimax) {
            minimax = max_ligne;
        }
    }

   return minimax;
}

int main() {
    int n, m, i, j;

  /* Saisie des dimensions */
    printf("Entrer le nombre de lignes : ");
    scanf("%d", &n);

  printf("Entrer le nombre de colonnes : ");
    scanf("%d", &m);

  int mat[100][100];

  /* Saisie de la matrice */
    printf("Entrer les elements de la matrice :\n");
    for(i = 0; i < n; i++) {
        for(j = 0; j < m; j++) {
            scanf("%d", &mat[i][j]);
        }
    }

   /* Calcul du MiniMax */
    int result = MiniMax(mat, n, m);

  /* Affichage du résultat */
    printf("Le MiniMax de la matrice est : %d\n", result);

  return 0;
}
