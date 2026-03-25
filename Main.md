import java.util.List;

public class Main {
    public static void main(String[] args) {

        HardwareRepository repo = new HardwareRepository();
        List<Hardware> hardwareList = repo.getAllHardware();

        int laptops16 = 0;
        int laptops32 = 0;
        int phones50 = 0;

        System.out.println("=== Hardware Masterlist ===");

        for (Hardware hw : hardwareList) {

            // MASTERLIST PRINT (polymorphism in action)
            System.out.println(
                hw.getClass().getSimpleName() + " - " + hw.getFormattedSpec()
            );

            // Audit
            if (hw instanceof Laptop) {
                if (hw.getSpecValue() == 16) laptops16++;
                if (hw.getSpecValue() == 32) laptops32++;
            } 
            else if (hw instanceof Phone) {
                if (hw.getSpecValue() == 50) phones50++;
            }
        }

        System.out.println("\n=== Inventory Summary ===");
        System.out.println("Total 16GB Laptops: " + laptops16);
        System.out.println("Total 32GB Laptops: " + laptops32);
        System.out.println("Total 50MP Phones: " + phones50);
    }
