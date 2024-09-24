### The Factory Method pattern defines an interface or abstract class for creating objects in a superclass but allows subclasses to alter the type of objects to be created. Use NetBeans to create a Java program that implements this design pattern. Name your project TestFactory.

1. Create an abstract superclass named Laptop. Any subclass of an abstract class must either implement all of the abstract methods in the superclass or be declared abstract itself. Copy the code below.

       abstract class Laptop { 
 
       public abstract int getRAM();
 
       public abstract int getSSD();
 
        public abstract String getCPU();
 
        public String toString() {

        return "RAM="+this.getRAM()+"GB, SSD="+this.getSSD()+", CPU="+this.getCPU();

        }
  
        }


2. Create a subclass named Minimum that extends your superclass. In this class, declare three (3) private variables with the following names and data types:

- ram (int)
- ssd (int)
- cpu (String)


3. Copy the code below for the constructor of your Minimum class. This constructor has three (3) parameters: ram, ssd, and cpu. Parameters are separated by commas as seen below.

            public Minimum(int ram, int ssd, String cpu){
  
            this.ram=ram;
  
            this.ssd=ssd;
  
             this.cpu=cpu;

              }


4. Create three (3) public getter methods named after the abstract methods in your superclass. These methods should return the value of the instance variables. Ex. return this.ram;

5. Add another subclass named Recommended that also extends the same superclass. This class shall have the same content with your Minimum class.

6. Add a class named LaptopFactory. Copy the code below for its method.


        public static Laptop getSpecs(String type, int ram, int ssd, String cpu){
 
        if("min".equalsIgnoreCase(type))
   
        return new Minimum(ram, ssd, cpu);

        else if("reco".equalsIgnoreCase(type))
 
        return new Recommended(ram, ssd, cpu);

        return null;

        }



7. Use the public class named TestFactory to execute your Factory Method pattern implementation. In its main method, instantiate a Laptop object named min. Copy the code below.

                  Laptop min = LaptopFactory.getSpecs("min", 8, 256, "i5-12450Hz");



8. Instantiate another Laptop object named reco. Follow the syntax above but use the following values for the 2nd to 4th parameter: 16, 512, i7-12700Hz

9. Display the content of the two (2) objects in separate lines.


SAMPLE OUTPUT:

Minimum Specs:

RAM=8GB, SSD=256, CPU=i5-12450Hz

Recommended Specs:

RAM=16GB, SSD=512, CPU=i7-12700Hz
