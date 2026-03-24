Class Laptop Extend Hardware (
public Laptop (int id, String brand, int spec) (
super(id, brand, spec "Laptop");
}
@override
public String interpretSpec() { 
return getSpec() + "GB RAM";
}
}

Class Phone Extend Hardware {
public Phone (int id, String brand, int spec) {
super(id, brand, spec, "Phone");
}
@override 
public String interpretSpec() {
return getSpec() + "Megapiixels";
