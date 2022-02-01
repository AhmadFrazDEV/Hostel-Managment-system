# Hostel-Managment-system
#include<iostream>
#include<stdlib.h>
using namespace std;

	// All variables
	string login , pswd; 
	int option;
	int days;
	int stdnum;
	double aggregate;
	// All variables

	// All Globle arrys
		string std_names[100];
		string std_marks_fsc[100];
		string std_marks_ecat[100];
		float agg[100]; 
		string mess_menu[100];
		string mess_day[100];
		
	// All Globle Arrys

// All Funtions

void header_of_hostal();
void login_box();
void menu();
void Details_of_students();
void display_list();
double Aggregate(int idx);
void input_sorting();
void room_allocation_sorting();
void display();
int find_largest_index(int i);
void mess_menu();
void display_menu();

// All Funtions

main()
{
	header_of_hostal();
	login_box();
	
	string users[2] = {"Admin" , "Student"};
	string password[2] = {"admin@123" , "student@123"};
	
	cout<<"Login As....(Admin / student)...";
	cin>>login;
	
	if(login==users[0])
	{
		
		cout<<"Enter your password.....";
		cin>>pswd;
		if(pswd==password[0])
		{
			menu();
			cout<<"Your option.....";
		 	cin>>option;
		 	
		 	if(option==1)
		 	{
		 		Details_of_students();	
		 		
		 		
			}
		// --------------------------------------------	
			menu();
			cout<<"Your option.....";
		 	cin>>option;
		 	
		 	if(option==3)
		 	{
		 		for(int i=0 ; i<stdnum ; i++)
		 		{
		 				float agg[i] = Aggregate(i);
				}
				for(int i=0  ;i<stdnum ; i++)
				{
					cout<<"Aggregate of"<<" "<<std_names[i]<<" "<<agg[i]<<endl;
				}
		 		
		 		
			}
			
		//-----------------------------------------------	
			
			if(option == 4)
			{
				input_sorting();
			}
			
		//-----------------------------------------------
		
			if(option == 7)
			{
				mess_menu();	
			}	
		
		//----------------------------------------------	
		}
	}
	
}

void header_of_hostal()
{	//header_of_hostal
	cout<<"\t\t"<<"###############################################################"<<endl;
	cout<<"\t\t"<<"#               HOSTEL MANAGEMENT SYSTEM                      #"<<endl;
	cout<<"\t\t"<<"###############################################################"<<endl;
}	//header_of_hostal

void login_box()
{
	cout<<"\t\t"<<"###############################################################"<<endl;
	cout<<"\t\t"<<"#                     LOGIN BOX                               #"<<endl;
	cout<<"\t\t"<<"###############################################################"<<endl;
}

void menu()
{	// menu
	cout<<"Main Menu"<<endl;
		cout<<"========================================================================================="<<endl;
		
		cout<<"Press 1 to Enter/Display Detail students"<<endl;
		cout<<"Press 2 to Modify/Remove the student’s data"<<endl;
		cout<<"Press 3 to Aggregates of Students"<<endl;
		cout<<"Press 4 to Display the Room Allocation according to the students Aggregates"<<endl;
		cout<<"Press 5 to Enter the Total Fees of Students"<<endl;
		cout<<"Press 6 to Add Fines for Students"<<endl;
		cout<<"Press 7 to Enter the Mess Menu and Prices of dishes"<<endl;
		cout<<"Press 8 for Done and again Login"<<endl;
}	// menu


void Details_of_students()
{	//Details_of_students
	
	cout<<"How many students do you want to enroll.....";
	cin>>stdnum;
	for(int i=0 ; i<stdnum; i++)
	{
		cout<<"Enter the"<<" "<<i+1<<" "<<"student name.....";
		cin>>std_names[i];
	}
	
	cout<<"#####################################################################"<<endl;
	
	for(int i=0 ; i<stdnum; i++)
	{
		cout<<"Enter the marks of FSC of"<<" "<<std_names[i]<<" "<<".....";
		cin>>std_marks_fsc[i];
	}
	
	cout<<"#####################################################################"<<endl;
	
	for(int i=0 ; i<stdnum; i++)
	{
		cout<<"Enter the marks of ECAT of"<<" "<<std_names[i]<<" "<<".....";
		cin>>std_marks_ecat[i];
	}
	
	cout<<"#####################################################################"<<endl;
	
	cout<<"Press L to see Students Details.....";
	char l;
	if(l==l)
	{
		display_list();
	}
	
}	//Details_of_students


void display_list()
{
	cout<<"NAME"<<"\t\t"<<"FSC MARKS"<<"\t\t"<<"ECAT MARKS"<<endl;
	
	for(int i=0 ; i<stdnum ; i++)
	{
		cout<<std_names[i]<<"\t\t"<<std_marks_fsc[i]<<"\t\t"<<std_marks_ecat[i]<<endl;
	}
}

double Aggregate(int idx)
{	//Aggregate
	
	aggregate = ((std_marks_ecat[idx]*100.0/400.0)*0.30) + ((std_marks_fsc[idx]*100.0/1100.0)*0.70);
	return aggregate;
	
}	//Aggregate

int find_largest_index(int i)
{	//find_largest_index
	int large = -1;
	int index;
	for(int i=0 ; i<stdnum ; i++)
	{
		if(agg[i]>large)
		{
			large = agg[i];
			index = i;
		}
	}
	return index;
} 	//find_largest_index
void display()
{	//display
	cout<<"NAME"<<"\t\t"<<"AGGREGATE"<<endl;
	for(int i=0 ; i<stdnum ; i++)
	{
		cout<<std_names<<"\t\t"<<agg[i];
	}
}	//display

void input_sorting()
{	// input_sorting
	
	int temp;
int index;
for(int i=0 ;i<stdnum ; i++)
{
	index = find_largest_index(i);
	temp = agg[i];
	agg[i] = agg[index];
	agg[index] = temp;
}

display();
	
}	//input_sorting

void display_menu(int days)
{	//display_menu

	cout<<"DAYS"<<"\t\t"<<"DISHES"<<endl;
	for(int i=0 ; i<days ; i++)
	{
		cout<<mess_day[i]<<"\t\t"<<mess_menu<<endl;
	}
	
}	//display_menu
void mess_menu()
{	//mess_menu
	for(int i=0 ; i<days ; i++)
	{
		cout<<"DAY...";
		cin>>mess_day[i];
		cout<<"DISH...";
		cin>>mess_menu[i];
		
	}
	display_menu(days);
}	//mess_menu
