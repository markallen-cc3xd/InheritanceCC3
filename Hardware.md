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


// Main class (NO SQL here)
public class Main {
    public static void main(String[] args) {

        Hardware[] devices = {
                new Laptop(16),
                new Laptop(32),
                new Laptop(16),
                new Laptop(32),
                new Laptop(16),
                new Phone(16),
                new Phone(48),
                new Phone(50),
                new Phone(48),
                new Phone(50)
        };

        int count16GB = 0;
        int count32GB = 0;
        int count16MP = 0;
        int count48MP = 0;
        int count50MP = 0;

        // Single loop
        for (Hardware device : devices) {

            device.displaySpec();

            if (device instanceof Laptop) {
                Laptop l = (Laptop) device;

                if (l.matchesQuery("ram=16")) count16GB++;
                if (l.matchesQuery("ram=32")) count32GB++;

            } else if (device instanceof Phone) {
                Phone p = (Phone) device;

                if (p.matchesQuery("mp=16")) count16MP++;
                if (p.matchesQuery("mp=48")) count48MP++;
                if (p.matchesQuery("mp=50")) count50MP++;
            }
        }

        // Results
        System.out.println("\nCounts:");
        System.out.println("16GB RAM Laptops: " + count16GB);
        System.out.println("32GB RAM Laptops: " + count32GB);
        System.out.println("16MP Phones: " + count16MP);
        System.out.println("48MP Phones: " + count48MP);
        System.out.println("50MP Phones: " + count50MP);
    }
}
