#include <stdio.h>
#include <string.h>
#include "../include/medical.h"

void load(Medicine m[] , int *n){
    FILE *fp = fopen("inventory.txt" , "r");
    *n = 0;
    if (!fp) return;
    
    while (fscanf(fp , "%d %s %d %f" , 
    &m[*n].id , m[*n].name , &m[*n].qty , &m[*n].price) == 4)

    (*n)++;
    fclose(fp);

}

void SaveToFile(Medicine m[] , int n) {
    FILE *fp = fopen("inventory.txt" , "w");
    if (!fp) return;
    
    for (int i = 0; i < n; i++)
    fprintf(fp , "%d %s %d %.2f\n" , m[i].id , m[i].name , m[i].qty , m[i].price);

    fclose(fp);
    
}

void add(Medicine m[], int *n) {
    printf("medicine name: ");
    scanf("%d", &m[*n].id);      
    
    printf("Name: ");
    scanf("%s", m[*n].name);   
    
    printf("Qty: ");
    scanf("%d", &m[*n].qty);   
    
    printf("Price: ");
    scanf("%f", &m[*n].price);
    (*n)++;                              
    printf("Added.\n");                          
}

void view(Medicine m[] , int n){

    if (n == 0)
    {
        printf("Empty!\n");
        return;
    }
    
    for ( int i = 0; i < n; i++)
    {
        printf("%d %s %d %.2f" , m[i].id , m[i].name , m[i].qty , m[i].price);
        return;
    }
    printf("Not Found.\n");
}

void search(Medicine m[] , int n){
    int id;
    printf("Enter ID: ");
    scanf("%d" , &id);

    for (int i = 0; i < n; i++)
    if (m[i].id == id)
    {
        printf("%d %s %d %.2f\n" , m[i].id , m[i].name , m[i].qty , m[i].price);
        return;
    }

    printf("Not Found.\n");
}

void update(Medicine m[] , int n){
    int id , op;
    printf("ID: ");
    scanf("%d" , &id);

    for (int i = 0; i < n; i++)
    if (m[i].id == id)
    {
        printf("Change(+/-): ");
        scanf("%d" , op);

        m[i].qty += op;
        if (m[i].qty < 0) m[i].qty = 0;
        
        printf("Updated.\n");
        return;
    }
    printf("Not Found.\n");
}

void del(Medicine m[] , int *n){
    int id , pos = -1;
    printf("ID to delete: ");
    scanf("%d" , &id);

    for (int i = 0; i < *n; i++)
    if (m[i].id == id) pos = i;
    
    if (pos == -1) {
        printf("Not Found.\n");
        return;
    }

    for (int i = pos; i < *n - 1; i++)
    m[i] = m[i + 1];

    (*n)--;
    printf("Deleted.\n");
}

int main(){
    Medicine m[MAX];
    int n = 0 , ch;

    load (m , &n);

    while (1)
    {
        printf("\n1.Add 2.View 3.Search 4.Update 5.Delete 6.Exit\nChoice:");
        scanf("%d" , &ch);

        if (ch == 6)
        {
            SaveToFile(m , n);
            break;
        }
        switch (ch)
        {
        case 1: add (m , &n); break;
        case 2: view(m , n); break;
        case 3: search(m , n); break;
        case 4: update(m , n); break;
        case 5: del(m , &n); break;
        default: printf("Invalid.\n");
        
    }
    
}
return 0;
}
