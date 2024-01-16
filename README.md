package gst_calculator;

import java.util.ArrayList;
import java.util.Scanner;

public class Calculator{

String partNumber, partDescription;
int quantity;
double price;

public String getPartNumber()
{
    return partNumber;
}

public void setPartNumber(String partno)
{
    this.partNumber=partno;
}

public String getPartDescription()
{
    return partDescription;
}

public void setPartDescription(String partDescription)
{
    this.partDescription=partDescription;
}

public int getQuantity()
{
    return quantity;
}

public void setQuantity(int quantity)
{
    this.quantity=(quantity>=0)?quantity:0;
}

public double getPrice()
{
    return price;
}

public void setPrice(double price)
{
    this.price=(price>=0)?price:0;
}

public double getInvoiceAmount()
{
    return this.quantity * this.price;
}
     public static void main(String []args)
     {
          Scanner input = new Scanner (System.in);
          String partno,partdescription;
          int quantity; double price;
          ArrayList<Calculator> arr=new ArrayList<Calculator>();
          System.out.print("Enter the part name:");
          partno= input.nextLine();
          System.out.print("Enter the part description:");
          partdescription= input.nextLine();
          System.out.print("Enter the unit price:");
          price= input.nextDouble();
          System.out.print("Enter the quantity:");
          quantity= input.nextInt();
          Calculator obj=new Calculator();
          obj.setPartNumber(partno);
          obj.setPartDescription(partdescription);
          obj.setQuantity(quantity);
          obj.setPrice(price);
          arr.add(obj);
          
         String ans="y";

         while(ans.equals("y"))
         {
              System.out.print("Do you have another item:");
              ans= input.next();
              if(ans.equals("y"))
              {
                    System.out.print("Enter the part name:");
                    partno= input.next();
                    System.out.print("Enter the part description:");
                    partdescription= input.next();
                    System.out.print("Enter the unit price:");
                    price= input.nextDouble();
                    System.out.print("Enter the quantity:");
                    quantity= input.nextInt();
                    obj=new Calculator();
                    obj.setPartNumber(partno);
                    obj.setPartDescription(partdescription);
                    obj.setQuantity(quantity);
                    obj.setPrice(price);
                    arr.add(obj);
               }
               else
               {
                    System.out.println("The Invoice details:");
                    System.out.println("Item\tQuantity\tunit Price\tTotalPrice");
                    System.out.println("==============================================");
                    double total=0, tax=0;
                    for(int i=0;i<arr.size();i++)
                    {
                       System.out.println(arr.get(i).getPartNumber() +"\t"+ arr.get(i).getQuantity() +"\t"+arr.get(i).getPrice() +"\t"+arr.get(i).getInvoiceAmount());
                       total+=arr.get(i).getInvoiceAmount();
                    }
                    
                    tax=(total * 15)/100;
                    System.out.println("\nGrand total : "+total);
                    System.out.println("Tax(15%): "+tax);
                    System.out.println("Total to pay : "+ (total+tax));
              }             
         }
     }
}

