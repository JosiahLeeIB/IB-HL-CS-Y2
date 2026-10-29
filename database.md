```java
import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintWriter;
import java.util.HashSet;
import java.util.Scanner;
import java.util.ArrayList;
import java.util.Collections; 
class act{
    public static void main(String[] args) throws FileNotFoundException {
        Scanner file = new Scanner(new File("extended-iris.data"));
        int missingerror=0;
        int typeerror = 0;
        int classerror = 0;
        int negativeerror = 0;
        int setosa = 0;
        int versicolor = 0;
        int virginica = 0;
        PrintWriter a = new PrintWriter("clean-data");
        HashSet<String> entries = new HashSet<String>();
        int repeaterror = 0;
        while(file.hasNextLine()){
            boolean hasError = false;
            String line = file.nextLine().trim();
            String[] divided = line.split(",");
            String flower = divided[4].trim();
            for (int i = 0; i < 4; i++) {
                try {
                    double value = Double.parseDouble(divided[i]);
                    if (value < 0) {
                        negativeerror++;
                        hasError = true;
                    }

                } catch (Exception e) {
                }
            }
            if (!entries.add(line)) {
                repeaterror++;
                hasError = true;
            }
            if(divided.length != 5){
                missingerror++;
                hasError = true;
            }
            for (int i = 0; i < divided.length; i++) {
                if (divided[i].trim().isEmpty()) {
                    missingerror++;
                    hasError = true;
                }
            }
            if(!flower.equalsIgnoreCase("Iris-setosa")&&!flower.equalsIgnoreCase("Iris-versicolor")&&!flower.equalsIgnoreCase("Iris-virginica")){
                classerror++;
                hasError = true;
            }
            if(divided.length==5){
                for(int i = 0; i<4;i++){
                    try {
                        Double doubleYes = Double.parseDouble(divided[i]);
                    } catch (NumberFormatException e) {
                        typeerror++;
                        hasError = true;
                    }
                }
            }
            if (!hasError) {
                a.println(line);
                if(flower.equals("Iris-setosa")) {
                    setosa++;
                } else if (flower.equals("Iris-versicolor")) {
                    versicolor++;
                } else if (flower.equals("Iris-virginica")) {
                    virginica++;
                }
            }
        }
        a.close();
        System.out.println("missing: "+ missingerror);
        System.out.println("incorrect type: "+ typeerror);
        System.out.println("class invalid: "+ classerror);
        System.out.println("repeated data: "+ repeaterror);
        System.out.println("negative:"+ negativeerror);
        System.out.println("virginica present: "+ virginica);
        System.out.println("setosa present: "+setosa);
        System.out.println("versicolor present: "+versicolor);
        stats();
    }
    public static void stats() throws FileNotFoundException{
        Scanner file = new Scanner(new File("clean-data"));
        ArrayList<Double> petalLength = new ArrayList<Double>();
        ArrayList<Double> petalWidth = new ArrayList<Double>();
        ArrayList<Double> sepalLength = new ArrayList<Double>();
        ArrayList<Double> sepalWidth = new ArrayList<Double>();
        while(file.hasNextLine()){
            String line = file.nextLine();
            String[] divided = line.split(",");
            petalLength.add(Double.parseDouble(divided[0]));
            petalWidth.add(Double.parseDouble(divided[1]));
            sepalLength.add(Double.parseDouble(divided[2]));
            sepalWidth.add(Double.parseDouble(divided[3]));
        }
        file.close();
        Collections.sort(petalLength);
        Collections.sort(petalWidth);
        Collections.sort(sepalLength);
        Collections.sort(sepalWidth);
        System.out.println("PL");
        calculate(petalLength);
        System.out.println("PW");
        calculate(petalWidth);
        System.out.println("SL");
        calculate(sepalLength);
        System.out.println("SW");
        calculate(sepalWidth);


    }
    public static void calculate(ArrayList<Double> a){
        int n = a.size();

        double sum = 0;
        for (double value : a) {
            sum += value;
        }
        double mean = sum / n;


        double median;
        if (n % 2 == 0) {
            median = (a.get(n / 2 - 1) + a.get(n / 2)) / 2;
        } else {
            median = a.get(n / 2);
        }

        double min = a.get(0);
        double max = a.get(n - 1);


        double squaredDifferences = 0;
        for (double value : a) {
            squaredDifferences += Math.pow(value - mean, 2);
        }

        double q1 = findMedian(a, 0, n / 2);
        double q3;

        if (n % 2 == 0) {
            q3 = findMedian(a, n / 2, n);
        } else {
            q3 = findMedian(a, n / 2 + 1, n);
        }


        double iqr = q3 - q1;


        double lowerFence = q1 - 1.5 * iqr;
        double upperFence = q3 + 1.5 * iqr;


        int outliers = 0;

        for (double value : a) {
            if (value < lowerFence || value > upperFence) {
                outliers++;
            }
        }

        System.out.println("Q1: " + q1);
        System.out.println("Q3: " + q3);
        System.out.println("IQR: " + iqr);
        System.out.println("Number of outliers: " + outliers);
        double standardDeviation = Math.sqrt(squaredDifferences / n);
        System.out.println("mean: "+mean);
        System.out.println("median: "+median);
        System.out.println("min: "+min);
        System.out.println("max: "+max);
        System.out.println("stddev: "+standardDeviation);
    }
    public static double findMedian(ArrayList<Double> values, int start, int end) {
        int n = end - start;

        if (n <= 0) {
            return Double.NaN;
        }

        if (n % 2 == 0) {
            return (values.get(start + n / 2 - 1)
                    + values.get(start + n / 2)) / 2.0;
        } else {
            return values.get(start + n / 2);
        }
    }

}



```
