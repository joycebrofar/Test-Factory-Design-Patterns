                            /*
                                    * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
                                    * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Main.java to edit this template
                             */
                                          package testfactory;
                            /**
                                    *
                                    * @author MSI
                                          */
                                                 public class TestFactory {
                             /**
                                   * @param args the command line arguments
                            */
                                                     public static void main(String[] args) {
                                    // TODO code application logic here
                                                 Laptop min = LaptopFactory.getSpecs("min", 8, 256, "i5-12450Hz");
                                                 Laptop reco = LaptopFactory.getSpecs("reco", 16, 512, "i7-12700Hz");
        
                                    System.out.println("Minimum Specs:");
                                    System.out.println(min.toString());
        
                                    System.out.println("Recommended Specs:");
                                    System.out.println(reco.toString());
                                }    
                            }

                                   abstract class Laptop {
                                     public abstract int getRAM();
                                     public abstract int getSSD();
                                     public abstract String getCPU();

                              @Override
                                     public String toString() {
                                       return "RAM="+this.getRAM()+"GB, SSD="+this.getSSD()+", CPU="+this.getCPU();
                                     }  
                                   }

                            class Minimum extends Laptop{
                                       private int ram;
                                       private int ssd;
                                       private String cpu;
    
                                       public Minimum(int ram, int ssd, String cpu){
                                           this.ram=ram;
                                           this.ssd=ssd;
                                           this.cpu=cpu;
                                       }
    
                                @Override
                                       public int getRAM(){return this.ram;}
    
                                @Override
                                          public int getSSD(){return this.ssd;}
    
                                @Override
                                          public String getCPU(){return this.cpu;}
                            }

                                   class Recommended extends Laptop{
                                       private int ram;
                                       private int ssd;
                                       private String cpu;
    
                                public Recommended(int ram, int ssd, String cpu){
                                           this.ram=ram;
                                           this.ssd=ssd;
                                           this.cpu=cpu;
                                }
    
                         @Override
                                public int getRAM(){return this.ram;}
    
                         @Override
                                public int getSSD(){return this.ssd;}
    
                         @Override
                                public String getCPU(){return this.cpu;}
                     }
                            class LaptopFactory{    
                         public static Laptop getSpecs(String type, int ram, int ssd, String cpu){
                                    if("min".equalsIgnoreCase(type))
                                    return new Minimum(ram, ssd, cpu);
                                    else if("reco".equalsIgnoreCase(type))
                                    return new Recommended(ram, ssd, cpu);
                                    return null;
                         }
                     }
