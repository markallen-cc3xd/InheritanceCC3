// Superclass
class Hardware {
    private int spec; // encapsulated

    public Hardware(int spec) {
        this.spec = spec;
    }

    public int getSpec() {
        return spec;
    }

    public void displaySpec() {
        System.out.println("Spec: " + spec);
    }
}

// Subclass Laptop
class Laptop extends Hardware {

    public Laptop(int ram) {
        super(ram);
    }

    @Override
    public void displaySpec() {
        System.out.println(getSpec() + "GB RAM");
    }

    // "SQL-like" condition method
    public boolean matchesQuery(String query) {
        // Simulating: SELECT * FROM Laptop WHERE ram = X
        if (query.equalsIgnoreCase("ram=16")) {
            return getSpec() == 16;
        } else if (query.equalsIgnoreCase("ram=32")) {
            return getSpec() == 32;
        }
        return false;
    }
}

// Subclass Phone
class Phone extends Hardware {

    public Phone(int cameraMP) {
        super(cameraMP);
    }

    @Override
    public void displaySpec() {
        System.out.println(getSpec() + " Megapixels");
    }

    // "SQL-like" condition method
    public boolean matchesQuery(String query) {
        // Simulating: SELECT * FROM Phone WHERE cameraMP = X
        if (query.equalsIgnoreCase("mp=16")) {
            return getSpec() == 16;
        } else if (query.equalsIgnoreCase("mp=48")) {
            return getSpec() == 48;
        } else if (query.equalsIgnoreCase("mp=50")) {
            return getSpec() == 50;
        }
        return false;
    }
}
