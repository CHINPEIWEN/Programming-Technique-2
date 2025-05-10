# Programming-Technique-2
/*Group Syntaxion
Group member:
CHIN PEI WEN (A23CS0065)
NAZATUL NADHIRAH BINTI SABTU (A23CS0144)
NURUL ATHIRAH SYAFIQAH BINTI MOHD RAZALI (A23CS0163)
TAN ZHAO HONG (A23CS0188)*/

#include <iostream> 
#include <string> 
#include <limits> 
#include <ctime> 
#include <iomanip> 
using namespace std; 
 
template <typename T1, typename T2> 
class Profile { 
private: 
    T1 name; 
    T2 age; 
public: 
    void setName(T1 n) { name = n; } 
    void setAge(T2 a) { age = a; } 
    T1 getName() { return name; } 
    T2 getAge() { return age; } 
}; 
 
class SelfAssessment 
{ 
    private: 
        int d = 0, a = 0, s = 0; 
    public: 
        int scale; 
        void test()  
        { 
            cout << "Please enter a number from 0 to 3 for each statement:" << endl; 
            auto getValidInput = [](const string& prompt) 
            { 
                int value; 
                while (true) 
                { 
                    cout << prompt; 
                    cin >> value; 
                    if (cin.fail()||value < 0 || value > 3)  
                    { 
                        cin.clear();  
                        cin.ignore(numeric_limits<streamsize>::max(), '\n');  
                        cout << "Invalid input. Please enter a number from 0 to 3.\n"; 
                    }  
                    else  
                    { 
                        cin.ignore(numeric_limits<streamsize>::max(), '\n');  
                        break;  
                    } 
            } 
            return value; 
        }; 
 
            scale = getValidInput("1. I found it hard to wind down: "); 
            d += scale; 
            a += scale; 
 
            scale = getValidInput("2. I was aware of dryness of my mouth: "); 
            d += scale; 
            s += scale; 
 
            scale = getValidInput("3. I couldn't seem to experience any positive feeling at all: "); 
            a += scale; 
            s += scale; 
 
            scale = getValidInput("4. I experienced breathing difficulty (e.g., excessively rapid breathing, breathlessness in the absence of physical exertion): "); 
            d += scale; 
            s += scale; 
 
            scale = getValidInput("5. I found it difficult to work up the initiative to do things: "); 
            a += scale; 
            s += scale; 
 
            scale = getValidInput("6. I tended to over-react to situations: "); 
            d += scale; 
            a += scale; 
 
            scale = getValidInput("7. I experienced trembling (e.g., in the hands): "); 
            d += scale; 
            s += scale; 
 
            scale = getValidInput("8. I felt that I was using a lot of nervous energy: "); 
            d += scale; 
            a += scale; 
 
            scale = getValidInput("9. I was worried about situations in which I might panic and make a fool of myself: "); 
            d += scale; 
            s += scale; 
 
            scale = getValidInput("10. I felt that I had nothing to look forward to: "); 
            a += scale; 
            s += scale; 
 
            scale = getValidInput("11. I found myself getting agitated: "); 
            d += scale; 
            a += scale; 
 
            scale = getValidInput("12. I found it difficult to relax: "); 
            d += scale; 
            a += scale; 
 
            scale = getValidInput("13. I felt down-hearted and blue: "); 
            a += scale; 
            s += scale; 
 
            scale = getValidInput("14. I was intolerant of anything that kept me from getting on with what I was doing: "); 
            d += scale; 
            a += scale; 
 
            scale = getValidInput("15. I felt I was close to panic: "); 
            d += scale; 
            s += scale; 
 
            scale = getValidInput("16. I was unable to become enthusiastic about anything: "); 
            a += scale; 
            s += scale; 
 
            scale = getValidInput("17. I felt I wasn't worth much as a person: "); 
            a += scale; 
            s += scale; 
 
            scale = getValidInput("18. I felt that I was rather touchy: "); 
            d += scale; 
            a += scale; 
 
            scale = getValidInput("19. I was aware of the action of my heart in the absence of physical exertion (e.g., sense of heart rate increase, heart missing a beat): "); 
            d += scale; 
            s += scale; 
 
            scale = getValidInput("20. I felt scared without any good reason: "); 
            d += scale; 
            s += scale; 
 
            scale = getValidInput("21. I felt that life was meaningless: ");
            a += scale; 
            s += scale; 
        } 
 
        int calDep() 
        { 
            return d; 
        } 
 
        int calAnx() 
        { 
            return a; 
        } 
 
        int calStr() 
        { 
            return s; 
        } 
 
        string getSeverity(int score) 
        { 
            if (score <= 14) return "Normal"; 
            else if (score <= 18) return "Mild"; 
            else if (score <= 25) return "Moderate"; 
            else if (score <= 33) return "Severe"; 
            else return "Extremely Severe"; 
        } 
}; 
 
class Guardian 
{ 
    private: 
        string name; 
        string phoneNum; 
    public: 
        void setName(string n) { name = n; } 
        void setPhoneNum(string p)  
        {  
            while(true)
            {
        	    cout << "Enter phone number (in format 01XXXXXXXXX): ";
			    cin >> phoneNum;
			    if(isValidPhoneNumber(phoneNum))
			    {
				    break;
			    } 
			    else
			    {
				    cout << "Invalid phone number. "
					     << "Your phone number must be in 10 or 11 digit without space or dash.\n";
			    }
		    }
        }
        bool isValidPhoneNumber(const string& phoneNum)
        {
    	    if(phoneNum.length()<10||phoneNum.length()>11)
    	    {
    		    return false;
		    }
		    for (char c:phoneNum)
		    {
			    if(!isdigit(c))
			    {
				    return false;
			    }
		    }
		    return true;
	    }
        string getName() { return name; } 
        string getPhoneNum() { return phoneNum; } 
}; 
 
class Location  
{ 
    private: 
        string HospName; 
    public: 
        Location (string n) : HospName(n) {} 
        string getHospName() { return HospName; } 
        void dispInfo()  
        { 
            cout << HospName << endl; 
        } 
}; 
 
class Professional 
{ 
    protected: 
        string name; 
        int experience; 
        Location* location; 
    public: 
        Professional(Location* loc):location(loc){} 
        string getName() { return name; } 
        string getExp() { return to_string(experience); } 
        virtual void descRole() = 0; 
        void dispLoc() 
        { 
            if (location) 
            { 
                cout << "Location: "; 
                location->dispInfo(); 
            } 
        } 
}; 
 
class Date
{ 
    private: 
        int day, month, year; 
    public: 
        Date() 
        { 
            time_t now = time(0); 
            struct tm* ltm = localtime(&now); 
            year = 1900 + ltm->tm_year; 
            month = 1 + ltm->tm_mon; 
            day = ltm->tm_mday;             
        } 
        bool isLeapYear(int year) 
        { 
            return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0); 
        } 
        int daysInMonth(int month, int year) 
        { 
            int days[] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}; 
            if(isLeapYear(year)) 
            { 
                days[1] = 29; 
            } 
            return days[month - 1]; 
        } 
        bool isValidDate(int day, int month, int year) 
        { 
            if (year < 1900 || month < 1 || month > 12 || day < 1 || day > daysInMonth(month, year)) 
            { 
                return false; 
            } 
            return true; 
        } 
        bool isAfterCurrentDate(int day, int month, int year) 
        { 
            time_t now = time(0); 
            struct tm* ltm = localtime(&now); 
            int currentYear = 1900 + ltm->tm_year; 
            int currentMonth = 1 + ltm->tm_mon; 
            int currentDay = ltm->tm_mday; 
            if (year > currentYear) 
            { 
                return true; 
            } 
            else if (year == currentYear && month > currentMonth) 
            { 
                return true; 
            } 
            else if (year == currentYear && month == currentMonth && day > currentDay) 
            { 
                return true; 
            } 
            return false; 
        } 
        void promptUserForDate() 
        { 
            int userDay, userMonth, userYear, userHour, userMin; 
            cout << "Enter the date(dd mm yyyy): "; 
            cin >> userDay >> userMonth >> userYear; 
            while (!isValidDate(userDay,userMonth,userYear)||!isAfterCurrentDate(userDay, userMonth, userYear)) 
            { 
                if (!isValidDate(userDay, userMonth, userYear)) 
                { 
                    cout << "Invalid date. Please try again: "; 
                } 
                else if (!isAfterCurrentDate(userDay, userMonth, userYear)) 
                { 
                    cout << "Date must be after today. Please try again: "; 
                } 
                cin >> userDay >> userMonth >> userYear; 
            } 
            setDate(userDay, userMonth, userYear); 
        } 
 
        void setDate(int day, int month, int year) 
        { 
            if (isValidDate(day, month, year) && isAfterCurrentDate(day, month, year)) 
            { 
                this->day = day; 
                this->month = month; 
                this->year = year; 
            } 
            else 
                cout << "Invalid date. Date not changed.\n"; 
        } 
        void printDate() 
        { 
            cout << day << "/" << month << "/" << year; 
        }         
}; 
  
class Time 
{
    private:
        int hour, minute;

    public:
        Time() : hour(0), minute(0) {}
        bool isValidTime(int hour, int minute) 
        { 
            if (hour < 8 || hour > 17 || minute < 0 || minute > 59) 
            { 
                return false; 
            } 
            return true; 
        } 
        void promptUserForTime() 
        {
            int userHour, userMin;
            cout << "Enter the time (0800 - 1700) in 24-hour format (hh mm): ";
            cin >> userHour >> userMin;
            while (!(userHour >= 8 && userHour <= 17 && userMin >= 0 && userMin <= 59))
		    {
                cout << "Invalid time. Please enter your time between 0800 to 1700: ";
                cin >> userHour >> userMin;
            }
            setTime(userHour, userMin);
        }

        void setTime(int hour, int minute) 
        {
            if ((hour >= 8 && hour <= 17) || (minute >= 0 && minute <= 59))
            {
                this->hour = hour;
                this->minute = minute;
            }
        }

        void printTime() 
	    {
            cout << hour << ":" << (minute < 10 ? "0" : "") << minute;
        }
};
 
class Appointment  
{ 
    private: 
        Date date; 
        Time time; 
        Location* location; 
        string doctor; 
    public: 
        void setDate(Date d)  
        {  
            date = d;  
        } 
        void setTime(Time t)  
        {  
            time = t;  
        } 
        void setLocation(Location* l) 
        {  
            location = l;  
        } 
        void setDoctor(string a) 
        { 
            doctor = a; 
        } 
        Date getDate() { return date; } 
        Time getTime() { return time; } 
        Location* getLocation() { return location; } 
        string getDoctor() {return doctor;} 
        void displayApmt(Profile<string, int>&p, Guardian& g, Professional* doc)  
        { 
            cout << "\n*******************Appointment*******************" << endl; 
            cout << "Name : " << p.getName() << endl; 
            cout << "Age : " << p.getAge() << endl; 
            if (p.getAge()<18) 
            { 
                cout << "Guardian information:\n"; 
                cout << "Name : " << g.getName() << endl; 
                cout << "Phone no: " << g.getPhoneNum() << endl; 
            } 
            cout << "Date : "; date.printDate(); cout << endl; 
            cout << "Time : "; time.printTime(); cout << endl; 
            cout << "Doctor : " << doc->getName() << endl;  
            doc->dispLoc(); 
            cout << "**************************************************\n" << endl;
        } 
}; 
 
class Counselor : public Professional 
{ 
public: 
    Counselor():Professional(new Location("KPJ Johor Specialist Hospital"))  
    { 
        name = "Mr Chan Kuan Foo"; 
        experience = 10;  
    } 
    void descRole() override  
    {  
        cout << "Counselor: " << name << endl;  
    } 
    void descInfo()  
    { 
        cout << "Counselor: " << name << endl;  
        cout << "Year of experience: " << experience << endl; 
        dispLoc(); 
    } 
}; 
 
class Psychiatrist : public Professional { 
public: 
    Psychiatrist():Professional(new Location("KPJ Selangor Specialist Hospital")) 
    {  
        name = "Dr Ashwin Chee Weng Seng"; 
        experience = 15;  
    } 
    void descRole() override  
    {  
        cout << "Psychiatrist: " << name << endl;  
    } 
    void descInfo()  
    { 
        cout << "Psychiatrist: " << name << endl;  
        cout << "Year of experience: " << experience << endl; 
        dispLoc(); 
    } 
}; 
 
class Psychologist : public Professional { 
public: 
    Psychologist():Professional(new Location("KPJ Melaka Specialist Hospital")) 
    { 
        name = "Dr Noorashikin Binti Ma'an"; 
        experience = 12;  
    } 
    void descRole() override  
    {  
        cout << "Psychologist: " << name << endl;  
    } 
    void descInfo()  
    { 
        cout << "Psychologist: " << name << endl;  
        cout << "Year of experience: " << experience << endl; 
        dispLoc(); 
    } 
}; 
 
 
class Disorder { 
protected: 
    string disorder; 
public: 
    virtual void displaySymptoms() = 0;  
}; 

class Stress:public Disorder{ 
public: 
    Stress() { disorder = "Stress"; } 
    void displaySymptoms() override { 
        cout << "What is stress?\n"; 
        cout << "Stress can be defined as a state of worry or mental tension caused by a difficult situation. "; 
        cout << "Stress is a natural response that prompts us to address challenges and threats in our lives. "; 
        cout << "Everyone experiences stress to some degree. The way we respond to stress, however, makes a big difference to our overall well-being." << endl; 
    } 
}; 
 
class Anxiety : public Disorder { 
public: 
    Anxiety() { disorder = "Anxiety"; } 
    void displaySymptoms() override { 
        cout << "What is anxiety?\n"; 
        cout << "Anxiety is a feeling of unease, such as worry or fear, that can be mild or severe. "; 
        cout << "Everyone has feelings of anxiety at some point in their life. For example, you may feel worried "; 
        cout << "and anxious about sitting an exam, or having a medical test or job interview. During times like these, feeling anxious can be perfectly normal.\n"; 
    } 
}; 
 
class Depression : public Disorder { 
public: 
    Depression() { disorder = "Depression"; } 
    void displaySymptoms() override { 
        cout << "What is depression?\n"; 
        cout << "Depression is a common mental disorder. It involves a low mood that lasts a long time, and affects your everyday life. "; 
        cout << "In its mildest form, depression can mean just being in low spirits. It doesn�t stop you leading your normal life "; 
        cout << "but makes everything harder to do and seem less worthwhile. At its most severe, major depression can be life-threatening "; 
        cout << "because it can make you feel suicidal or simply give up the will to live.\n"; 
    } 
}; 
 
int main() 
{ 
    Profile <string, int> user;  
    Stress s; Anxiety a; Depression d; 
    SelfAssessment patient; 
    Guardian guardian; 
    Date date; Time time; 
    Appointment appointment; 
    Professional* doc = nullptr; 
    Counselor counselor; Psychiatrist psychiatrist; Psychologist psychologist; 
    string name, location, num;  
    int age, option, option2, opt3, opt4, ans, state;  
    cout << "*** Mental Health Awareness ***\n" 
         << "User's profile:\n"  
         << "Name: "; 
    getline(cin,name);  
    cout << "Age: "; 
    cin >> age; 
    cin.ignore(); 
    user.setName(name); 
    user.setAge(age); 
    cout << endl; 
    do 
    { 
        cout << "Hi " << user.getName() << ", Welcome to Mental Health Awareness.\n" 
             << "1 - Disorder Information\n" 
             << "2 - Self Assessment\n" 
             << "3 - Exit\n" 
             << "Enter your option: "; 
        cin >> option; 
        cin.ignore(); 
        cout << endl; 
        switch (option) 
        { 
            case 1: 
            while (true) 
            { 
                cout << "Here is some disorder information we got for you :)\n" 
                     << "1 - Stress\n" 
                     << "2 - Anxiety\n" 
                     << "3 - Depression\n" 
                     << "4 - back to main page\n" 
                     << "Enter your option : "; 
                cin >> option2; 
                cin.ignore(); 
                cout << endl; 
                if (option2 == 1) 
                { 
                    s.displaySymptoms(); 
                    cout << endl; 
                } 
                else if (option2 == 2) 
                { 
                    a.displaySymptoms(); 
                    cout << endl; 
                }     
                else if (option2 == 3) 
                { 
                    d.displaySymptoms(); 
                    cout << endl; 
                } 
                else if (option2 == 4) 
                    break; 
            } 
            break; 
    case 2: 
        patient.test(); 
        cout << "\nAssessment Result:\n"; 
        cout << "Depression: " << patient.calDep() << " (" << patient.getSeverity(patient.calDep()) << ")\n"; 
        cout << "Anxiety: " << patient.calAnx() << " (" << patient.getSeverity(patient.calAnx()) << ")\n"; 
        cout << "Stress: " << patient.calStr() << " (" << patient.getSeverity(patient.calStr()) << ")\n"; 
        cout << endl; 
        do 
        { 
            cout << "Do you need appoinment ?\n 1 - yes 2 - no\nAnswer: "; 
            cin >> ans; 
            cin.ignore(); 
            cout << endl; 
            if (ans == 1) 
            { 
                if (user.getAge() <18) 
                { 
                    cout << "Please fill in your guardian information\n" 
                         << "Guardian name: "; 
                    getline(cin,name); 
                    guardian.setPhoneNum(num);
                    guardian.setName(name);  
                    cout << endl; 
                } 
            date.promptUserForDate(); 
            time.promptUserForTime(); 
            appointment.setDate(date); 
            appointment.setTime(time); 
            cout << endl;  
            while (true) 
            { 
                cout << "Available professionals: \n"; 
                cout << "1. "; counselor.descRole(); 
                cout << "2. "; psychologist.descRole(); 
                cout << "3. "; psychiatrist.descRole(); 
                cout << "Please choose a doctor:"; 
                cin >> opt3; 
                cout << endl; 
                switch (opt3) 
                { 
                    case 1: 
                    { 
                        counselor.descInfo(); 
                        doc = new Counselor(); 
                        break; 
                    } 
                    case 2: 
                    { 
                        psychologist.descInfo(); 
                        doc = new Psychologist(); 
                        break; 
                    } 
                    case 3: 
                    { 
                        psychiatrist.descInfo(); 
                        doc = new Psychiatrist(); 
                        break; 
                    } 
                    default: 
                        cout << "Invalid option.Please choose again: "; 
                        continue; 
                } 
                cout << "\nWould you like to proceed your appointment?\n" 
                     << "1-yes\n2-no,choose other professional\n3-back to the main page\nPlease enter your option: "; 
                cin >> opt4;   
                if (opt4 == 1) 
                { 
                    appointment.displayApmt(user,guardian,doc); 
                    delete doc; 
                    break; 
                } 
                else if (opt4 == 2) 
                { 
                    cout << "\nReturning to the professional list...\n"; 
                    continue; 
                } 
                else if (opt4 == 3) 
                { 
                    cout << "\nExiting to the main page...\n"; 
                    break; 
                } 
                else 
                { 
                    cout << "\nInvalid option.Please choose again.\n"; 
                } 
                 
            } 
            } 
            else if (ans == 2) 
            { 
                cout << "Exiting to the main page...\n"; 
                break; 
            } 
        } while (ans<1 || ans>2); 
        break; 
    case 3:  
        cout <<"Exiting the program...\nThank you for using this system. Have a nice day!"; 
        break; 
        } 
    } while (option!=3); 
    cout << endl; 
     
    system("pause"); 
    return 0; 
}
