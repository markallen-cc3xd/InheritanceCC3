public abstract class Hardware {
    protected int specValue;

    public Hardware(int specValue) {
        this.specValue = specValue;
    }

    public int getSpecValue() {
        return specValue;
    }

    public abstract String getFormattedSpec();
}
