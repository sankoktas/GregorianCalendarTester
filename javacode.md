This program does a lot of things with Gregorian Calendar

import java.util.GregorianCalendar;

import java.util.Scanner;

import java.util.Random;

public class KFS_GregorianCalendarTester_Main 

{
    
    public static void main(String[] args)
    
    {
        GregorianCalendar date = new GregorianCalendar(); //2nd objective
        
        int year = date.get(GregorianCalendar.YEAR);  
        System.out.println("Current year: " + year); //3rd objective

        int dayOfMonth = date.get(GregorianCalendar.DAY_OF_MONTH); //4th objective
        System.out.println("Current day of month: " + dayOfMonth);
        
        int month = date.get(GregorianCalendar.MONTH); //This code functions by printing the number of the month, not its name. Although Java Calendar is synchronized with local         time and date, API says, it doesn't follow ISO 8601 standards. Thus, January is month 0 in Java Calendar. Yet we don't use it in our daily lives. So, I add one to the           month the method gets. 
        System.out.println("Current month: " + (month+1)); //5th objective
        
        System.out.println("Current date: " + dayOfMonth + "/" + (month+1) + "/" + year);  //6th objective
        
        int dayOfWeek = date.get(GregorianCalendar.DAY_OF_WEEK); //Again, this code functions by printing the number of the day, not its name. In Gregorian Calendar Sunday is the first day of the week, per API. This means "1" in output means today is Sunday while "2" means Monday.  
        System.out.println("Current day of the week (Sunday is considered the first day): " + dayOfWeek); //7th objective
        
        int hourOfDay = date.get(GregorianCalendar.HOUR_OF_DAY); 
        int minutes = date.get(GregorianCalendar.MINUTE);
        System.out.println("Time in military format: " + hourOfDay + ":" + minutes); //8th objective
        
        GregorianCalendar eckertsBirthday = new GregorianCalendar(1919, 3, 9); 
        int eckertsDay = eckertsBirthday.get(GregorianCalendar.DAY_OF_MONTH);
        int eckertsMonth = eckertsBirthday.get(GregorianCalendar.MONTH);
        int eckertsYear = eckertsBirthday.get(GregorianCalendar.YEAR);
        System.out.println("Birthday of J. Presper Eckert: " + eckertsBirthday.get(GregorianCalendar.DAY_OF_MONTH) + "/" + (eckertsBirthday.get(GregorianCalendar.MONTH)+1) + "/" + eckertsBirthday.get(GregorianCalendar.YEAR)); //9th objective
        
        int eckertsAge = year - eckertsYear;
        System.out.println("Eckert would be " + eckertsAge + " years old if he were alive today."); //10th objective
                
        GregorianCalendar eckerts_next_birthday = new GregorianCalendar((year + 1), 3, 9);
        int y = eckerts_next_birthday.get(GregorianCalendar.DAY_OF_YEAR);
        int dayOfYear = date.get(GregorianCalendar.DAY_OF_YEAR);
        int remainingDays = (366 - dayOfYear) + y; //366 because February has 29 days in the following year
        System.out.println("There are " + remainingDays + " days to celebrate Eckert's birthday."); //11th objective 
        
        GregorianCalendar eminem = new GregorianCalendar(1972, 9, 17);
        GregorianCalendar ibra = new GregorianCalendar(1981, 9, 3);
        GregorianCalendar san = new GregorianCalendar(2002, 6, 28);
        int eminemYear = eminem.get(GregorianCalendar.YEAR);
        int ibraYear = ibra.get(GregorianCalendar.YEAR);
        int sanYear = san.get(GregorianCalendar.YEAR);
        int eminemAge = year - eminemYear;
        int ibraAge = year - ibraYear;
        int sanAge = year - sanYear;
        System.out.println("Age of Eminem: " + eminemAge);
        System.out.println("Age of Ibra: " + ibraAge);
        System.out.println("Age of Myself: " + sanAge); //12th objective
        
        int averageAge = (eminemAge + ibraAge + sanAge)/3;
        System.out.println("The average of these three ages: " + averageAge);//13th objective  
           
        GregorianCalendar rc_close_date = new GregorianCalendar(2021, 5, 22);
        int close = rc_close_date.get(GregorianCalendar.DAY_OF_YEAR);
        int summerHoliday = (366 - dayOfYear) + close; 
        System.out.println("RC closes on: " + rc_close_date.get(GregorianCalendar.DAY_OF_MONTH) + "/" + (rc_close_date.get(GregorianCalendar.MONTH) + 1) + "/" + rc_close_date.get(GregorianCalendar.YEAR)); 
        System.out.println("There are " + summerHoliday + " days left for the summer holiday!");  //14th objective 
        
        GregorianCalendar random_calendar = new GregorianCalendar();
        int random_year = randBetween(0, 2147483647); //from the birth of Jesus to maximum int Java allows 
        random_calendar.set(random_calendar.YEAR, random_year);
        int random_day = randBetween(1, random_calendar.getActualMaximum(random_calendar.DAY_OF_YEAR));
        random_calendar.set(random_calendar.DAY_OF_YEAR, random_day);
        System.out.println("Here is a random date: " + random_calendar.get(random_calendar.DAY_OF_MONTH) + "/" + (random_calendar.get(random_calendar.MONTH) + 1) + "/" + random_calendar.get(random_calendar.YEAR));//15th objective
        
        Scanner in = new Scanner(System.in);
        System.out.print("Please enter a date in day,month,year order without leaving any blanks between the numbers, bear in mind that you can write only up to 2147483647 and you should put zero in front of one digit months and days (example: 19051919 for 19 May 1919): ");
        String dateIn = in.nextLine();
        int p = dateIn.length();
        String user_day = dateIn.substring(0,2);
        String user_month = dateIn.substring(2,4);
        String user_year = dateIn.substring (4,p);
        System.out.println("Here is the date you entered: " + user_day + "/" + user_month + "/" + user_year); //16th objective
          
        GregorianCalendar myBirthday = new GregorianCalendar(2002, 5, 28);
        int birthday_weekday = myBirthday.get(myBirthday.DAY_OF_WEEK);
        CalendarUtils birthday = new CalendarUtils(); 
        System.out.println("I was born on a "+  birthday.getWeekday(birthday_weekday)); //17th objective 
        
        int birthday_year = myBirthday.get(myBirthday.YEAR);
        int birthday_month = myBirthday.get(myBirthday.MONTH);
        int birthday_day = myBirthday.get(myBirthday.DAY_OF_MONTH);
        System.out.println("My birthday: "+  birthday.getMonth(birthday_month) + " " + birthday_day + ", " + birthday_year); //18th objective 
        
        GregorianCalendar gc1000 = new GregorianCalendar();
        myBirthday.add(GregorianCalendar.DAY_OF_MONTH, 10000);
        int my_tenthousandth_birthday_day = myBirthday.get(GregorianCalendar.DAY_OF_MONTH);
        int my_tenthousandth_birthday_month = myBirthday.get(GregorianCalendar.MONTH);
        String my_tenthousandth_birthday_month_as_a_string = birthday.getMonth(my_tenthousandth_birthday_month);
        int my_tenthousandth_birthday_year = myBirthday.get(GregorianCalendar.YEAR);
        System.out.println("10,000th day of my life is on: " + my_tenthousandth_birthday_month_as_a_string + " " + my_tenthousandth_birthday_day + ", " + my_tenthousandth_birthday_year); //19th objective
        
        GregorianCalendar todays_date = new GregorianCalendar(2020, 11, 9);
        //If I gotta practise 10,000 hours with 1 hour per day, we need 10,000 days.
        todays_date.add(GregorianCalendar.DAY_OF_MONTH, 10000);
        int expert_day = todays_date.get(GregorianCalendar.DAY_OF_MONTH);
        int expert_month = todays_date.get(GregorianCalendar.MONTH);
        String expert_month_as_a_string = birthday.getMonth(expert_month);
        int expert_year = todays_date.get(GregorianCalendar.YEAR); 
        System.out.println("If I were to start practising football now, and practise for one hour every day without fail, I would be expert on: " + expert_month_as_a_string + " " + expert_day + ", " + expert_year); //20.1 objective 
        //I will be able to practise 5 hours per day
        GregorianCalendar todays_date_number_two = new GregorianCalendar(2020, 11, 9);
        int x = 5;
        int total_days_for_fast_expertise = 10000/5;
        todays_date_number_two.add(GregorianCalendar.DAY_OF_MONTH, total_days_for_fast_expertise);
        int fast_expert_day = todays_date_number_two.get(GregorianCalendar.DAY_OF_MONTH);
        int fast_expert_month = todays_date_number_two.get(GregorianCalendar.MONTH);
        String fast_expert_month_as_a_string = birthday.getMonth(expert_month);
        int fast_expert_year = todays_date_number_two.get(GregorianCalendar.YEAR); 
        System.out.println("If I were to start practising football now, and practise for " + x + " hours every day without fail, I would be expert on: " + fast_expert_month_as_a_string + " " + fast_expert_day + ", " + fast_expert_year); //20.2 objective 
    }
    public static int randBetween(int start, int end) 
    {
        return start + (int)Math.round(Math.random() * (end - start));
    }
   
}
