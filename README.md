# abstractions
public abstract class Doping { 
protected double price; 
protected double[] taxes; 
public double[] getTaxes() { 
return taxes; 	
}

public void setTaxes(double[] taxes) { 
this.taxes = taxes; 	
}
public double getPrice() { 
return price; 	
}

public void setPrice(double price) { 
this.price = price; 	
}

 public abstract double calculate(); 
 }

public class TopOfListDoping extends Doping { 
public TopOfListDoping(double price) { 
super.setPrice(price); 	
}

@Override public double calculate() { 
return super.getPrice() + super.getPrice() * 0.35; 	}

}

public class UptodateDoping extends Doping { 
public UptodateDoping(double price, double[] taxes)
{ 
super.setPrice(price); super.setTaxes(taxes); 	}

@Override public double calculate() { 		
return calculateTaxes() + commisionRate(); 	}

private double calculateTaxes() { 		
double totalTaxValue = 0; for(int i=0; i < super.getTaxes().length; i++) { totalTaxValue += super.getTaxes()[i]; 		}
return totalTaxValue; 	}

private double commisionRate() { return super.getPrice() * 0.2; 	}
}
