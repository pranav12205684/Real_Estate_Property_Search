#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX_PROPERTIES 100
typedef struct {
    char address[50];
    char city[50];
    char state[50];
    int price;
} Property;
Property properties[MAX_PROPERTIES];
int numProperties = 0;
void addProperty(char* address, char* city, char* state, int price) {
    Property p;
    strcpy(p.address, address);
    strcpy(p.city, city);
    strcpy(p.state, state);
    p.price = price;
    properties[numProperties++] = p;
}
void searchProperties(int minPrice, int maxPrice, char* city, char* state) {
    int i;
    printf("Search Results:\n");
    for (i = 0; i < numProperties; i++) {
        Property p = properties[i];
        if (p.price >= minPrice && p.price <= maxPrice && strcmp(p.city, city) == 0 && strcmp(p.state, state) == 0) {
            printf("%s, %s, %s - %d\n", p.address, p.city, p.state, p.price);
        }
    }
}
int main() {
    addProperty("Plot No-458, Pragathi Nagar", "Hyderabad", "Telangana",600000);
    addProperty("Plot No-302, KPHB", "Hyderabad", "Telangana", 850000);
    addProperty("Plot No-961, Ameerpet", "Hyderabad", "Telangana", 1100000);
    addProperty("Plot No-1024, Jyoti Chowk", "Jalandhar", "Punjab",400000);
    addProperty("Plot No-658, N M Town", "Jalandhar", "Punjab", 650000);
    addProperty("Plot No-463, Kamal Vihar Phase 2", "Jalandhar", "Punjab", 900000);
    addProperty("Plot No-1234, Bhagatpura", "Phagwara", "Punjab",400000);
    addProperty("Plot No-357, Model Town", "Phagwara", "Punjab", 650000);
    addProperty("Plot No-597, Urban Estate", "Phagwara", "Punjab", 900000);
    addProperty("Plot No-134, Civil Lines", "Ludhiana", "Punjab",500000);
    addProperty("Plot No-857, Sarabha Nagar", "Ludhiana", "Punjab", 750000);
    addProperty("Plot No-248, Sunder Nagar", "Ludhiana", "Punjab", 1000000);
    int minPrice, maxPrice;
    char city[50], state[50];
    printf("Enter minimum price(in lakhs): ");
    scanf("%d", &minPrice);
    printf("Enter maximum price(in lakhs): ");
    scanf("%d", &maxPrice);
    printf("Enter city(Hyderabad or Jalandhar or Phagwara or Ludhiana): ");
    scanf("%s", city);
    printf("Enter state: ");
    scanf("%s", state);
    searchProperties(minPrice, maxPrice, city, state);   
    return 0;
}
