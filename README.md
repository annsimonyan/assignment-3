// assignment3
#include <iostream>
#include <string>
using namespace std;

 string Month[12] = {"January", "February", "March", "April", "May", "June", 
 "July","August","September","October","November","December" };
  string makes (int a, string s) 
{
	while (a!=0)
	{
		s+=char (a%10+'0');
		a=a/10;
	}
	for (int i=0; i<s.size()/2; i++)
	{
		swap (s[s.size()-i-1],s[i]);
	}
	return s;
}
 class Date { 
     protected:
     int day;
     string month;
     int year;
     
     public:
     Date () ;
     Date (int,string,int);
     void initialize (void );
     void get_formatted_date (void);
  
 };

class Student: public Date
{   string firstname;
    string lastname;
    string faculty;
    int unique_number;
    string unique_num;
    string id;
    Date birth_date; 
   public:
     
     static int count;
     Student (string first_name, string last_name, string Faculty);
     Student ( Student& copydata);
     string get_first_name(void);
     string get_last_name(void);
     string get_faculty(void);
     string get_id(void);
     void set_birth_date(int Day, string Month, int Year);
};
 Date :: Date () 
  {  year = 1900;
     month = Month[0];
     day = 1 ;
 }
Date:: Date(int x,string y,int z) 
{
  day=x;
  month=y;
  year=z;
}
void Date::initialize (void )
{  int x=0;
 for (int i=0;i<=12;i++) {
     if (Month[i]==month) { x=1 ;}
 }
  if (x==0) {
      cout << "your month is incorrect"<< endl;
  }
  if (day<1 || day>=31) {     
    cout << "Invalid date"<< endl;
  }
  if (month==Month[1]) {
      if (day> 29 && day<31) {
       cout << "Invalid date"<< endl;
      }
 
  }   
}
void Date::get_formatted_date (void)
{
    cout << year <<"."<<month<<"-"<<day; 
}

int Student::count = 0;
Student:: Student (string first_name, string last_name, string Faculty) {
    firstname= first_name;
    lastname= last_name;
    faculty= Faculty;
    unique_number=count;
    count ++;
    
    makes (unique_number,unique_num);
    }
Student::Student ( Student& copyinfo){
    faculty= copyinfo.get_faculty();
    id=copyinfo.get_id();
}
string Student:: get_id(void) {
    
     string a= faculty;
     id = "AUA_<" + a+">_<"+unique_num+">";
     return id;
    
}
string Student:: get_first_name(void)
{
    return firstname;
}
string Student:: get_last_name(void)
{
    return lastname;
}
string Student::get_faculty(void) 
{
    return faculty;
}
void Student:: set_birth_date(int Day, string Month, int Year)
{
	day= Day;
	month=Month;
	year=Year;
}
int main(void)
{
  Student Aram("Aram", "Grigoryan", "CS"); 
  Aram.set_birth_date(12, 7, 1995);
Student d(Aram);
d.firstname("Ara");
d.lastname("Sargsyan");
d.birth_date(1, 5, 1995);

cout << "Below is the information about the registered students"<< endl;
cout << Aram.get_first_name() <<Aram.get_last_name<<" "<<Aram.get_faculty<< " " << Aram.get_id()<< :endl;
cout <<Aram.get_formatted_date() << endl;

cout << d.get_first_name() << " " << d.get_id()<<endl;
cout << d.get_birth_date() << endl;
}
