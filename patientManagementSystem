#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <conio.h>
#include <windows.h>


#define MAX 50
#define NEAREST_COUNT 2
#define MAX_COUNT 9999
#define PHARMACY_COUNT 5
#define EX_COUNT 13


void mainMenu();
void headMessage();
void welcomeDisplay();
void mainMenu();
void gotoxy (int x, int y);
void setColor();
void pharmacyMenu(); 
void wasMenu();
void finance();
void policlinic();



COORD coord = {0,0};

char password[10]={"firdevs"};

typedef struct{
    char id[12];
    char name[20];
	char surname[20];
	int operation;
	int age;
	char date[20];
	
}patient;

typedef struct {
    char name[20];
	char telno[20];
	char address[20];
	char isOpen[20];
}pharmacy;


pharmacy pharmacies[PHARMACY_COUNT] = {	"Faruk Eczanesi","02123162545","Istanbul/Turkey","Close", "Gul Eczanesi","02123635678","Istanbul/Turkey","Close",
										"Fakir Eczanesi","02123634245","Istanbul/Turkey","Close", "Nazar Eczanesi","02123632354","Istanbul/Turkey","Open",
										"IAU Eczanesi","02123631247","Istanbul/Turkey","Open" };
										
typedef struct {
	int id;
	char name[20];
	char madeBy[20];
	int stockAmount;
	
}drug;

typedef struct{
	int ID;
	char exName[50];
	char docName[50];
	float cost;
}exFee;

exFee exFees[EX_COUNT] = {1, "Examination Sp. Psysician", "Fuat Ozukara", 450.36,
						  2, "Examination Pr. Psysician", "Sibel Dagverdi", 346.54,
						  3, "Examination Pra. Psysician", "Yasemin Koral", 212.00,			
						  4, "Normal Polyclinic", "Firdevs Samyeli", 95.45,
						  5, "Psychologist Session", "Mert Bozuka", 150.98, 
						  6, "Medical Board Report", "Chris Tanriverdi", 43.78,
						  7, "Physical Therapy Examination", "Necmettin Ok", 154.05,
						  8, "Eye Examination", "Salih Huysuz", 112.48,
						  9, "Chest Diseases Examination", "Merve Pekmez", 243.00,
						  10, "Heart disease Examination", "Nalan Soyutükenmez", 185.47,
						  11, "Orthopedic Examination", "Cilek Karpuzgil", 146.87,
						  12, "Gynecology Examination", "Sabiha Turk", 164.44,
						  13, "Urology Examination", "Mehmet Evren", 98.72};

void gotoxy (int x, int y)
{
coord.X = x; coord.Y = y; 
SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), coord);
}

void setColor() {
	system("color 80");	
}

void headMessage(){
	
	system("cls");
    printf("\t\t\t###########################################################################");
    printf("\n\t\t\t############                                                   ############");
    printf("\n\t\t\t############      Patient Management System v1.1               ############");
    printf("\n\t\t\t############                                                   ############");
    printf("\n\t\t\t###########################################################################");
    printf("\n\t\t\t---------------------------------------------------------------------------\n");
	
}
void welcomeDisplay(){
		
	printf("\n\n\n");
    printf("\n\t\t\t\t        *********************************************");
    printf("\n\t\t\t\t                      System Information             ");
    printf("\n\t\t\t\t        =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=");
    printf("\n\t\t\t\t        =              Lambda                       =");
    printf("\n\t\t\t\t        =                Version 1.1                =");
    printf("\n\t\t\t\t        =                                           =");
    printf("\n\t\t\t\t        =              Copyright 2020               =");
    printf("\n\t\t\t\t        =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=\n");
    printf("\n\t\t\t\t        *********************************************\n");
    printf("\n\n\n\t\t\t Press any key to continue.....");
    getch();
}

int dbExists(char db[30])
{
    FILE *file;
    if ((file = fopen(db, "ab")))
    {
        fclose(file);
        return 1;
    }
    return 0;
}
int dbExistsP(char db[30])
{
    FILE *file;
    if ((file = fopen(db, "r")))
    {
        fclose(file);
        return 1;
    }
    return 0;
}
void savePatient(patient item){
	FILE *file;
	if ((file = fopen("patient.dat", "ab")) == NULL) {
		printf("File doesnt work!");
		exit(1);
	}
	fwrite(&item, sizeof(patient), 1, file);
	fclose(file);
}
patient *patientLoad(int *size) {
    FILE *file;
	if ((file = fopen("patient.dat", "rb")) == NULL) {
		printf("File doesnt work!");
		exit(1);
	}
	patient *list;
	int count = 100;
	list = (patient*) malloc(count * sizeof(patient));
	patient item;
	int exists = 0;
	for (*size = 0; fread(&item, sizeof(patient), 1, file); ++*size) {
		exists = 1;
		if (*size >= count) {
			count += 100;
			list = (patient*) realloc(list, count * sizeof(patient));
		}
		list[*size] = item;
	}
	fclose(file);
	*size += exists;
	list = (patient*) realloc(list, *size * sizeof(patient));
	return list;
}
void patientReg(){
	
	system("cls");  	
	
	patient item;
	gotoxy(40,3);
	printf("Patient ID : ");
	scanf("%s",item.id);
	gotoxy(60,5);
	printf("\nPatient Name : ");
	scanf("%s",item.name);
	gotoxy(40,7);
	printf("\nPatient Surname : ");
	scanf("%s",item.surname);
	gotoxy(40,9);
	while ((getchar()) != '\n');
	printf("\nOperation : ");
	scanf("%d",&item.operation);
	while ((getchar()) != '\n');
	gotoxy(40,11);
	printf("\nAge : ");
	scanf("%d",&item.age);
	while ((getchar()) != '\n');
	gotoxy(40,13);
	printf("\nDate : ");
	scanf("%s",item.date);

	savePatient(item);		
	
	gotoxy(40,15);
	printf("\nPress any button to save it...");
	if(getch()) {
		policlinic();
	}
}
void pressCC(){
		
		char dName[30];
		int amountBx,doze;
		gotoxy(30,7);
		printf("Input drug name : ");
		scanf("%s",dName);
		gotoxy(30,9);
		printf("Input amount of box : ");
		scanf("%d",&amountBx);
		gotoxy(30,11);
		printf("Input daily doze : ");
		scanf("%d",&doze);
	
}

void prescrip(){
	
	system("cls");
	
	int flag=0;
	char idP[11];
	FILE *file;
	gotoxy(30,3);
	printf("ID : ");
	scanf("%s",idP);
	file = fopen("patient.dat","rb");
	rewind(file);
	patient item;	
	while(fread(&item,sizeof(patient),1,file)){
		if(strcmp(item.id,idP)==0){
		gotoxy(30,5);	
		printf("%s %s",item.name,item.surname);
		pressCC();
		
		printf("Do you want to add new drug? Y/N");
		if(getch()=='y'){
			pressCC();
		}else{
			
			gotoxy(40,12);
			printf("Press enter to print it.");
			if(getch()){
				policlinic();
			}
		}
		
		flag=1;	
		}
			
	}if(flag==0){
		
		printf("No record found!");
		if(getch()){
			policlinic();
		}
	}
	fclose(file);
	
}
void listPatients(int count){
	system("cls");
	
	int size;
	patient *list = patientLoad(&size);	
	gotoxy(20,5);
	printf("%-20s %-15s %-15s %-15s %-15s %-15s\n","ID","Name","Surname","Age","Operation","Date");
	gotoxy(20,6);
	printf("%-20s %-15s %-15s %-15s %-15s %-15s\n","----","-------","--------","----","-----------","-------");
	
	for(int i = 0; i < count && i < size; ++i) {
		gotoxy(20, 8 + i);
		printf("%-20s %-15s %-15s %-15d %-15d %-15s\n", list[i].id, list[i].name, list[i].surname, list[i].age, list[i].operation, list[i].date);
	}
	free(list);
	
	gotoxy(50,25);
	printf("Press any button to back Policlinic Menu... ");
	if(getch()){
		policlinic();
	}
}
void policlinic(){
	
	system("cls");
	
	char policlinicDB[30]= "patient.dat";
	dbExists(policlinicDB);
	
	gotoxy(30,5);
	printf("Policlinic");
	gotoxy(30,9);
	printf("1. Patient Registration");
	gotoxy(30,11);
	printf("2. Prescription");
	gotoxy(30,13);
	printf("3. List Patients");
	gotoxy(30,15);
	printf("4. Back to Main Menu");
	gotoxy(40,18);
	printf("Enter your choice : ");
	switch(getch()){
		case '1':
			patientReg();
			break;
		case '2':
			prescrip();
			break;
		case '3':
			listPatients(MAX_COUNT);
			break;
		case '4':
			mainMenu();
			break;
		default :
			getch();
			policlinic();
			break;
	}
}
void exMenu(){
	
	system("cls");
	
	int i;
	gotoxy(20,5);
	printf("%-10s %-30s %-30s %-30s\n","ID","Examination Name","Doctor Name","Cost");
	gotoxy(20,6);
	printf("%-10s %-30s %-30s %-30s\n","----","-------------","------------","-------");
	for(i=0;i<EX_COUNT;++i){
		gotoxy(20, 8 + i);
		printf("%-10d %-30s %-30s %-30f\n",exFees[i].ID, exFees[i].exName, exFees[i].docName, exFees[i].cost);
	}
	
	gotoxy(30,24);
	printf("Press any button to back Finance Menu");
	if(getch()){
		finance();
	}
}
void patientCost(){
	system("cls");
	int flag=0;
	char idPol[11];
	FILE *file;
	
	printf("ID : ");
	scanf("%s",idPol);
	file = fopen("patient.dat","rb");
	rewind(file);
	patient item;	
	while(fread(&item,sizeof(patient),1,file)){
		if(strcmp(idPol,item.id)==0){
			for(int i=0;i<EX_COUNT;++i){
				if(item.operation == exFees[i].ID){
					gotoxy(30,5);
				printf("%-15s %-15s %-15s %-15s\n","ID","Name","Surname","Total Cost");
						gotoxy(30,6);
						printf("%-15s %-15s %-15s %-15s\n","-------------","------------","-------","----------");
						gotoxy(30,8);
						printf("%-15s %-15s %-15s   %-15f\n", item.id, item.name, item.surname, exFees[i].cost);
			}
			}
			
		
		flag=1;	
		}
			
	}if(flag==0){
		
		printf("No record found!");
		if(getch()){
			policlinic();
		}
	}
	fclose(file);
	
	
}
void finance(void){
	
	system("cls");
	gotoxy(30,5);
	printf("Finance");
	gotoxy(30,9);
	printf("1. Examination Fee");
	gotoxy(30,11);
	printf("2. Patient Total Cost");
	gotoxy(30,13);
	printf("3. Back to Main Menu");
	gotoxy(40,16);
	printf("Enter your choice : ");
	switch(getch()){
		case '1':
			exMenu();
			break;
		case '2':
			patientCost();
			break;
		case '3':
			mainMenu();
			break;
		default :
			getch();
			finance();
			break;
	}
}
void saveDrugs(drug item){
	FILE *file;
	if ((file = fopen("drug.dat", "ab")) == NULL) {
		printf("File doesnt work!");
		exit(1);
	}
	fwrite(&item, sizeof(drug), 1, file);
	fclose(file);
}

void addDrugs(){
	
	system("cls");
	
	drug item;
	gotoxy(40,3);
	printf("Drug ID : ");
	scanf("%d",&item.id);
	gotoxy(60,5);
	printf("\nDrug Name : ");
	scanf("%s",item.name);
	gotoxy(40,7);
	printf("\nManufacturer : ");
	scanf("%s",item.madeBy);
	gotoxy(40,9);
	printf("\nStock Amount : ");
	scanf("%d",&item.stockAmount);

	saveDrugs(item);		
	
	gotoxy(40,12);
	printf("\nPress any button to save it...");
	if(getch()) {
		wasMenu();
	}
}
drug *drugLoad(int *size) {
    FILE *file;
	if ((file = fopen("drug.dat", "rb")) == NULL) {
		printf("File doesnt work!");
		exit(1);
	}
	drug *list;
	int count = 100;
	list = (drug*) malloc(count * sizeof(drug));
	drug item;
	int exists = 0;
	for (*size = 0; fread(&item, sizeof(drug), 1, file); ++*size) {
		exists = 1;
		if (*size >= count) {
			count += 100;
			list = (drug*) realloc(list, count * sizeof(drug));
		}
		list[*size] = item;
	}
	fclose(file);
	*size += exists;
	list = (drug*) realloc(list, *size * sizeof(drug));
	return list;
}
void searchDrugs(){
	
	system("cls");
	FILE *file;
	int d,flag=0;
	char s[20];
	
	gotoxy(40,3);
	printf("Search Drug");
	gotoxy(40,8);
	printf("1. Search By ID");
	gotoxy(40,10);
	printf("2. Search By Name");
	gotoxy(40,12);
	printf("3. Back to WareHouse Management Menu");
	if((file = fopen("drug.dat","rb+")) == NULL){
		printf("File doesnt work!");
		exit(1);
	}
	rewind(file);
	switch(getch()){
		case '1':
			system("cls");
			printf("Input the Drug ID : ");
			scanf("%d",&d);
			printf("Searching... It takes a time!");
			drug item;
			while(fread(&item, sizeof(drug),1,file)){
				if(item.id == d){
						gotoxy(30,5);
						printf("%-15s %-15s %-15s %-15s\n","Drug ID","Drug Name","Manufacturer","Stock Amount");
						gotoxy(30,6);
						printf("%-15s %-15s %-15s %-15s\n","-------------","------------","-------","----------");
						gotoxy(30,7);
						printf("%-15d %-15s %-15s   %-15d\n", item.id, item.name, item.madeBy, item.stockAmount);
						flag = 1;
				}
			}if(flag == 0){
				printf("No record found!");
			}
			printf("Please enter any button to back");
			if(getch()){
				searchDrugs();
			}
			break;
		case '2':
			system("cls");
			printf("Input the Drug Name");
			scanf("%s",s);
			printf("Searching... It takes a time!");
			while(fread(&item,sizeof(drug),1,file)){
				if(strcmp(item.name,s)==0){
					gotoxy(30,5);
						printf("%-15s %-15s %-15s %-15s\n","Drug ID","Drug Name","Manufacturer","Stock Amount");
						gotoxy(30,6);
						printf("%-15s %-15s %-15s %-15s\n","-------------","------------","-------","----------");
						gotoxy(30,7);
						printf("%-15d %-15s %-15s   %-15d\n", item.id, item.name, item.madeBy, item.stockAmount);
						flag = 1;
				}
			}if(flag == 0){
				printf("No record found!");
			}
			printf("Please enter any button to back");
			if(getch()){
				searchDrugs();
			}
			break;
		case '3':
			wasMenu();
			break;
		
		default:
			getch();
			searchDrugs();
			break;
		
	}
	fclose(file);
	
}
void viewDrugs(int count){
	system("cls");
	
	int size;
	drug *list = drugLoad(&size);	
	gotoxy(30,5);
	printf("%-15s %-15s %-15s %-15s\n","Drug ID","Drug Name","Manufacturer","Stock Amount");
	gotoxy(30,6);
	printf("%-15s %-15s %-15s %-15s\n","-------------","------------","-------","----------");
	
	for(int i = 0; i < count && i < size; ++i) {
		gotoxy(30, 8 + i);
		printf("%-15d %-15s %-15s   %-15d\n", list[i].id, list[i].name, list[i].madeBy, list[i].stockAmount);
	}
	free(list);
	
	gotoxy(50,25);
	printf("Press any button to back Drug Menu");
	if(getch()){
		wasMenu();
	}
}
void wasMenu(){
	
	system("cls");
	char wasDB[30]="drug.dat";
	if(dbExists(wasDB)){
		
	}
	
	
	gotoxy(40,3);
	printf("Warehouse Management");
	gotoxy(40,6);
	printf("1.Add Drugs");
	gotoxy(40,8);
	printf("2.Search Drugs");
	gotoxy(40,10);
	printf("3.View All Drugs");
	gotoxy(40,12);
	printf("4.Back to Main Menu");
	gotoxy(50,15);
	printf("Enter your choice : ");
	switch(getch()){
		case '1':
			addDrugs();
			break;
		case '2':
			searchDrugs();
			break;
		case '3':
			viewDrugs(MAX_COUNT);
			break;
		case '4':
			mainMenu();
			break;
		default:
			printf("Invalid Number! Please re-enter a valid number... ");
			if(getch()) {
				wasMenu();
				break;	
			}
		}
	
}
void save(pharmacy item) {
    FILE *file;
	if ((file = fopen("pharmacy.dat", "ab")) == NULL) {
		printf("File doesnt work!");
		exit(1);
	}
	fwrite(&item, sizeof(pharmacy), 1, file);
	fclose(file);
}

pharmacy *load(int *size) {
    FILE *file;
	if ((file = fopen("pharmacy.dat", "rb")) == NULL) {
		printf("File doesnt work!");
		exit(1);
	}
	pharmacy *list;
	int count = 100;
	list = (pharmacy*) malloc(count * sizeof(pharmacy));
	pharmacy item;
	int exists = 0;
	for (*size = 0; fread(&item, sizeof(pharmacy), 1, file); ++*size) {
		exists = 1;
		if (*size >= count) {
			count += 100;
			list = (pharmacy*) realloc(list, count * sizeof(pharmacy));
		}
		list[*size] = item;
	}
	fclose(file);
	*size += exists;
	list = (pharmacy*) realloc(list, *size * sizeof(pharmacy));
	return list;
}

void addPharmacy() {
	system("cls");
	
	pharmacy item;
	gotoxy(40,3);
	printf("Pharmacy Name : ");
	scanf("%s",item.name);
	gotoxy(60,5);
	printf("\nTelephone No : ");
	scanf("%s",item.telno);
	gotoxy(40,7);
	printf("\nAddress : ");
	scanf("%s",item.address);
	gotoxy(40,9);
	printf("\nOpen/Close : ");
	scanf("%s",item.isOpen);

	save(item);		
	
	gotoxy(40,12);
	printf("\nPress any button to save it...");
	if(getch()) {
		pharmacyMenu();
	}
}
	
void viewPharmacy(int count) {
	system("cls");
	
	int size;
	pharmacy *list = load(&size);
	gotoxy(30,5);
	printf("%-15s %-15s %-15s %-15s\n","Pharmacy Name","Telephone No","Address","Open/Close");
	gotoxy(30,6);
	printf("%-15s %-15s %-15s %-15s\n","-------------","------------","-------","----------");
	
	for(int i = 0; i < count && i < size; ++i) {
		gotoxy(30, 8 + i);
		printf("%-15s %-15s %-15s   %-15s\n", list[i].name, list[i].telno, list[i].address, list[i].isOpen);
	}
	free(list);
	
	gotoxy(50,25);
	printf("Press any button to back Pharmacy Menu");
	if(getch()){
		pharmacyMenu();
	}
}

void pharmacyMenu() {
	system("cls");
	char pharmacyDB[30] = "pharmacy.dat";
	
	if (!dbExistsP(pharmacyDB))
		for (int i = 0; i < PHARMACY_COUNT; ++i)
			save(pharmacies[i]);
	
	gotoxy(40,3);
	printf("PHARMACY");
	gotoxy(40,6);
	printf("1.Add Pharmacy");
	gotoxy(40,8);
	printf("2.View The Nearest Pharmacies");
	gotoxy(40,10);
	printf("3.View All Pharmacies");
	gotoxy(40,12);
	printf("4.Back to Main Menu");
	switch(getch()){
		case '1':
			addPharmacy();
			break;
		case '2':
			viewPharmacy(NEAREST_COUNT);
			break;
		case '3':
			viewPharmacy(MAX_COUNT);
			break;
		case '4':
			mainMenu();
			break;
		default:
			printf("Invalid Number! Please re-enter a valid number... ");
			if(getch()) {
				pharmacyMenu();
				break;	
			}
		}
}

void close(){
	
	system("cls");
	
	printf("\n\n\n");
	printf("\n\t\t\t\t        ***********************************************\n");
	printf("\n\t\t\t\t                                   #                     ");
    printf("\n\t\t\t\t                                 ## ##                   ");
    printf("\n\t\t\t\t                                ##   ##                  ");
    printf("\n\t\t\t\t                   #           ##     ##                 ");
    printf("\n\t\t\t\t                 ## ##        ##       ##                ");
    printf("\n\t\t\t\t               ##    ##      ##         ##               ");
    printf("\n\t\t\t\t        #######       ##    ##           ##############  ");
    printf("\n\t\t\t\t                       ## ##                             ");
    printf("\n\t\t\t\t                         #                               ");
    printf("\n\t\t\t\t                                                       \n");
    printf("\n\t\t\t\t        ***********************************************\n");
    
    gotoxy(30,20);
    printf("Burak Kececi B1905.010047 Computer Engineering 1.Year Final Project\n\n");
}
void mainMenu(){
	
	system("cls");
	
	gotoxy(40,3);
	printf("MAIN MENU");
	
	gotoxy(40,5);	
	printf("1. Policlinic");
	gotoxy(40,7);	
	printf("2. Finance");
	gotoxy(40,9);
	printf("3. Warehouse and Stock Management");
	gotoxy(40,11);
	printf("4. Pharmacy");
	gotoxy(40,13);
	printf("5. Close Application ");
	
	gotoxy(40,18);
	printf("Enter your choice : ");
	switch(getch())
	{
	case '1':
		policlinic();
		break;
	case '2':
		finance(); 
		break;
	case '3':
		wasMenu();
		break;
	case '4':
		pharmacyMenu();
		break;
	case '5':
		close();
		break;
	default:
	{
		gotoxy(10,20);
		printf("\nINVALID NUMBER! Please enter a valid number... ");
		if(getch())
			mainMenu();
		}	
	}
}
void Password(void){
	
	system("cls");
	char mm[25]=" Password Protected ";
	char chr,passw[10];
	int i=0,j;
	gotoxy(30,4);
	for(j=0;j<20;j++)
	{
	Sleep(50);
	printf(">");
	}
	for(j=0;j<20;j++)
	{
	Sleep(50);
	printf("%c",mm[j]);
	}
	for(j=0;j<20;j++)
	{
	Sleep(50);
	printf("<");
	}
	gotoxy(40,8);
	printf("Enter Password : ");
	while(chr!=13){
			
		chr = getch();
		if(chr!=13){
			putch('*');
			passw[i]=chr;
			i++;
		}
	}
	passw[i] = '\0';
	if(strcmp(passw,password)==0){
		gotoxy(70,11);
		printf("Password matched.");
		gotoxy(45, 14);
		printf("Press any key to continue...");
		getch();
		mainMenu();
	}else{
		gotoxy(45,11);
		printf("INVALID PASSWORD!");
		getch();
		Password();
	}
	}
		
	
int main(){
	
	setColor();
	headMessage();
	welcomeDisplay();
	Password();
	mainMenu();
	
	return 0;
