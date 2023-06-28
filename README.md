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
public TopOfListDoping(double price) { super.setPrice(price); 	}

// "Doping" soyut sınıfından kalıtımla gelen, "calculate" isimli soyut metodu metot ezmesi yöntemiyle alt sınıf kendi ihtiyacına göre dolduruyor. // "TopOfList" isimli doping tipinde vergiler olmadığı için komisyon oranı eklenip ücret hesaplanıyor. Fakat, başka doping çeşitlerinde hesaplama farklı olabilir. @Override public double calculate() { 
return super.getPrice() + super.getPrice() * 0.35; 	}
}

public class UptodateDoping extends Doping { 
public UptodateDoping(double price, double[] taxes) { super.setPrice(price); super.setTaxes(taxes); 	}

// "Doping" soyut sınıfından kalıtımla gelen, "calculate" isimli soyut metodu metot ezmesi yöntemiyle alt sınıf kendi ihtiyacına göre dolduruyor. // "UptodateDoping" isimli doping tipinde vergiler fiyata dahil olduğu için komisyon oranı eklenip ve vergiler hesaplanıp ücret belirleniyor. // Görüldüğü gibi her doping çeşidinin fiyat hesaplama yöntemleri birbirinden farklıdır. Soyutlama ile sınıflara ait iç çalışma detayları gizlenmmiş oluyor. // Doping tiplerinde sadece "calculate" isimli fonksiyonu dış dünyaya açtık. Diğer tüm fonksiyonlar ve özellikler sınıf içinde kaldı. @Override public double calculate() { 		
return calculateTaxes() + commisionRate(); 	}

private double calculateTaxes() { 		
double totalTaxValue = 0; for(int i=0; i < super.getTaxes().length; i++) { totalTaxValue += super.getTaxes()[i]; 		}
return totalTaxValue; 	}

private double commisionRate() { return super.getPrice() * 0.2; 	}
}
