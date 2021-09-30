// Final-Project
 #include <stdio.h>
  #include <string.h>

struct Vehicle {
    char choice[255];
    int time;
    int amount;
    float cost;
    bool isActive;
};


Vehicle vehicles[20];
int total_vehicle = 0;


void choosevehicle(Vehicle v);
void showVehicles();
void showChoices();
void removeRequest();
void Menu();

int main() {
    Menu();
    return 0;
}

void showVehicles() {
    for(int i = 0; i < total_vehicle; ++i) {
        if(vehicles[i].isActive) {
            printf("%s %d %d %f", vehicles[i].choice, vehicles[i].time, vehicles[i].amount, vehicles[i].cost);
        }
        
		}
    }


void choosevehicle(Vehicle v) {
    strcpy(vehicles[total_vehicle].choice, v.choice);
    vehicles[total_vehicle].time = v.time;
    vehicles[total_vehicle].isActive = true;
    total_vehicle++;
}

void removerequest() {
    char nameToRemove[255];
    printf("Insert the request you want to remove: ");
    scanf("%[^\n]", nameToRemove); getchar();

    for(int i = 0; i < total_vehicle; i++) {
        if(strcmp(vehicles[i].choice, nameToRemove) == 0) {
            vehicles[i].isActive = false;
        }
    }
}

void showChoices() {
    puts("Menu");
    puts("1. Choose Vehicles");
  	puts("2. Show Vehicles");
  	puts("3. Remove Request");
	puts("4. Exit");
} 	


void Menu() {
    bool onApp = true;

    while(onApp) {
        
        showChoices();
        int choice = -1;

    do {
        printf(">> ");
        scanf("%d", &choice); getchar();
    } while(choice < 1 || choice > 4);

 	if(choice == 1) {
        Vehicle choosevehicles;
        printf("Type of vehicle: ");
        scanf("%[^\n]", choosevehicles.choice); getchar();
        
        printf("Time: ");
        scanf("%d", &choosevehicles.time); getchar();
        
        printf("Amount: ");
        scanf("%d", &choosevehicles.amount); getchar();
        
        printf("Cost: ");
        scanf("%f", &choosevehicles.cost); getchar();
            
        choosevehicle(choosevehicles);
        } 
		else if(choice == 2) {
            showVehicles();
        } 
		else if(choice == 3) {
            removerequest();
        } 
		else if(choice == 4) {
            printf("Thank You Visiting our app");
            onApp = false;
        }
    }
    
}
