#include<stdio.h>
#include<stdlib.h>
#include<dos.h>
#include<string.h>
#include <unistd.h>
struct item{
	char name[20];
	int quantity;
	
};
struct id{
    char cardname[20];
    int cardpin;
};
main()
{
	struct item menu[50];
  //Pin is 1234
	// ** ITEM NAME DECLARATION **
	strcpy(menu[0].name, "Biryani");
     strcpy(menu[1].name, "Butter chicken");
     strcpy(menu[2].name, "Chana Masala");
     strcpy(menu[3].name, "Chicken tikka masala");
     strcpy(menu[4].name, "Roti");
     strcpy(menu[5].name, "Dal Makhani");
     strcpy(menu[6].name, "Malai kofta");
     strcpy(menu[7].name, "Palak chicken");
     struct id card[20]; 
	FILE *fp,*f1;
	char a,q,ci[100];
	int pin,n,m,cp,i,k=0,o=0;
	printf("\t\tBill maker:\n");
	printf("Enter the pin:");
		scanf("%d",&pin);
	
	if(pin==1234)
		{
			start:
			system("cls");
			fp=fopen("orders.txt","a");
			f1=fopen("card_info.txt","a");
			// ** PRICE DECLARATION **
			int price[10]={300,400,500,250,50,300,400,150},total_price[50];
			float tax=0,total=0,sub=0,discount=0;
			for(i=0;i<8;i++)
				{
					total_price[i]=0;
				}
			system("color 07");
			// ** FOOD QUANTITY **
			for(i=0;i<8;i++)
				{
					menu[i].quantity=0;
				}
			do{
				printf("\tWelcome to Bill maker\n\t---------------------\n");
				printf("1.Item list\n");
				printf("2.Make a bill\n");
				printf("3.Create a discount card\n");
				printf("\nEnter choice:");
				scanf("%d",&n);
		
			switch(n)
				{
				case 1:{
					do{
						system("cls");
						printf("\t      MENU:\n -------------------------------\n");
			    		printf("   Item:                 Price:\n");
			   		 	printf(" -------------------------------\n");
						printf("0.Biryani               Rs.300\n");
						printf("1.Butter chicken        Rs.400\n");
						printf("2.Chana Masala          Rs.500\n");
						printf("3.Chicken tikka masala  Rs.250 \n");
						printf("4.Roti                  Rs.50 \n");
						printf("5.Dal Makhani           Rs.300 \n");
						printf("6.Malai kofta           Rs.400 \n");
						printf("7.Palak chicken         Rs.150\n");
						printf(" -------------------------------\n");
						printf("8.Exit to main screen\n\n");
						printf("Enter choice:");
							scanf("%d",&m);
						if(m!=8)
							{
								printf("Enter quantity of %s:",menu[m].name);
									scanf("%d",&menu[m].quantity);
								total_price[m]=price[m]*menu[m].quantity;
							}
						system("cls");
					}while(m!=8);
				break;
						}
				case 2:{
						system("cls");
						char l;
						printf("Do you have discount card(y/n):");
						scanf("%s",&l);
						if(l!='n' && l!='N')
						{
							printf("enter card id:");
							scanf("%s",ci);
							printf("Enter pin");
							scanf("%d",&cp);
							for(i=0;i<k;i++)
							{
								if(strcmp(card[i].cardname, ci) == 0 && card[i].cardpin==cp)
								{
									system("cls");
									system("color 02");
									printf("\n\tSuccessfully discount added");
									sleep(1);
									printf(".");
									sleep(1);
									printf(".");
									sleep(1);
									printf(".");
									sleep(2);
									system("cls");
									discount=50;
									
								}
								
						    }
						    if(discount!=50)
									{
										system("cls");
										system("color 04");
										printf("\n\tINVALID USER NAME (OR) PIN");
										sleep(2);
										goto start;
									}
						}
						system("color 02");
						o++;
						printf("\n\n\t\t         Bill:\n");
						printf("\t---------------------------------------\n");
						printf("\tOrder:%d\n",o);
						printf("\tItem             quantity        price\n");
						printf("\t---------------------------------------\n");
						if(menu[0].quantity!=0)
							{
								printf("\t%s                  %d         %d\n",menu[0].name,menu[0].quantity,total_price[0]);
							}
						if(menu[1].quantity!=0)
							{
								printf("\t%s           %d         %d\n",menu[1].name,menu[1].quantity,total_price[1]);
							}
						if(menu[2].quantity!=0)
							{
								printf("\t%s      	 %d         %d\n",menu[2].name,menu[2].quantity,total_price[2]);
							}
						if(menu[3].quantity!=0)
							{
								printf("\t%s    %d         %d\n",menu[3].name,menu[3].quantity,total_price[3]);
							}
						if(menu[4].quantity!=0)
							{
								printf("\t%s      	         %d         %d\n",menu[4].name,menu[4].quantity,total_price[4]);
							}
						if(menu[5].quantity!=0)
							{
								printf("\t%s      	 %d         %d\n",menu[5].name,menu[5].quantity,total_price[5]);
							}
						if(menu[6].quantity!=0)
							{
								printf("\t%s      	 %d         %d\n",menu[6].name,menu[6].quantity,total_price[6]);
							}
						if(menu[7].quantity!=0)
							{
								printf("\t%s      	 %d         %d\n",menu[7].name,menu[7].quantity,total_price[7]);
							}
						sub=total_price[0]+total_price[1]+total_price[2]+total_price[3]+total_price[4]+total_price[5]+total_price[6]+total_price[7];
						tax=(10/sub)*100;
						total=tax+sub;
						total=total-discount;
				 		printf("\t---------------------------------------\n");
				 		printf("\tsubtotal                         %.2f\n",sub);
				 		printf("\ttax                              %.2f\n",tax);
				 		if(discount!=0)
				 		{
				 		printf("\tDiscount                         %.2f\n",discount);	
						 }
				 		printf("\ttotal                            %.2f\n",total);
				 		printf("\t---------------------------------------\n");
				 		fprintf(fp,"\tBill:\n-------------------\nOrder:%d\n",o);
						for(i=0;i<8;i++)
							{
								if(menu[i].quantity>0)
									{
										fprintf(fp,"Item:%s quantity:%d price:%d\n",menu[i].name,menu[i].quantity,total_price[i]);
									}
							}
						fprintf(fp,"SubTotal=%.2f\nTax=%.2f\nDiscount=%.2f\nTotal=%.2f\n",sub,tax,discount,total);	 
					 	printf("Make another bill (y/n):");
						scanf("%s",&a);
					 	if(a!='n' && a!='N')
						 	{
						 		goto start;
							 }
						else{
							goto end;
							break;
							}
						}
				case 3:{
					printf("Create card id name:");
					scanf("%s",&card[k].cardname);
					printf("Create pin:");
					scanf("%d",&card[k].cardpin);
					fprintf(f1,"Card holder name:%s\nCard pin:%d\n",card[k].cardname,card[k].cardpin);
					k++;
					system("cls");
					break;
					
				}					
					}
				}while(n!=2);
	
	}// WRONG PIN CHANCE
	else
	{
		system("cls");
		system("color 04");
		printf("\n\n\t>>>>>WRONG PIN<<<<<\n\n");
		printf("Last chance:");
		scanf("%d",&pin);
		if(pin==1234)
			{
				goto start;
			}
		else
			{
				system("cls");
			printf("\n\n\t>>>>>WRONG PIN<<<<<\n\n");
			}
	}
	end:
	fclose(fp);
	fclose(f1);
	return 0;
}
