<h1>Quiz 1</h1>

```java
import java.util.Random;

public class ranNum{
    private Random rand = new Random();
    public int getNumber(){
        return rand.nextInt((257-0)+1)+0;
    }
}
```



<h1>Quiz 2</h1>

```java
public class IPv4Gen{
    private ranNum num = new ranNum();
    private String IP = "#";
    public String generate(){
        for(int i = 0; i < 4; i++) {
            IP += (num.getNumber());
            if(i!=3){
                IP+=".";
            }
        }
        return IP;
    }
}
```




<h1>Quiz 3</h1>

```java
public class check{
    public String test(String IP){
        String[] parts = IP.split(".");
        for (int i = 0; i < 4; i++) {
            if(Integer.parseInt(parts[i])>256){
                return "#False";
            }
        }
        return "#True";
    }
}
```



<h1>Quiz 4</h1>

```java
public class porter{
    private String[] service = {"http","https","playstation","ssh","ftp","mysql"};
    private String serviceA;
    private String[] ports = {"80","443","3479","22","20","3306"};
    private String IP;
    public porter(String c, String d){
        serviceA = c;
        IP = d;
    }
    public String build(){
        for(int i = 0; i<service.length;i++){
            if(serviceA == service[i]){
                return IP + "." + ports[i];
            }
        }
        return "service not on record table";
    }
}
```




<h1>Quiz 5</h1>

```java
public class dns{
    private String[] IP = {"127.0.0.1","142.250.72.14","7.7.7.7"};
    private String[] host = {"localhost","google.com","example.com"};
    private String IPcheck;
    public dns(String a){
        IPcheck = a;
    }
    public String lookup(){
        for(int i =0;i<host.length;i++){
            if(IPcheck == host[i]){
                return IP[i];
            }
        }
        return "Not found";
    }
}
```



<h1>Quiz 6</h1>

```java
public class filter{
    private String[] IP = {"127.0.0.1","142.250.72.14","7.7.7.7"};
    private String[] host = {"localhost","google.com","example.com"};
    private String[] whitelisted = {"127.0.0.1", "42.250.72.14","example.com"};
    private String check;
    public filter(String a){
        check = a;
    }
    public String checks(){
        for(int x = 0; x<whitelisted.length;x++){    
            if(check == whitelisted[x]){   
                for(int i = 0;i<IP.length;i++){
                    if(check == IP[i]){
                        return "accepted, IP: " + check + "host: " + host[i];
                    }
                }
                for(int y = 0;y<host.length;y++){
                    if(check == IP[y]){
                        return "accepted, IP: " + IP[y] + "host: " + check;
                    }
                }
            }
        }
        return "not whitelisted";
    }
}
```



<h1>Quiz 7</h1>

![IMG_7031](https://github.com/user-attachments/assets/2af3faed-3ff6-4c04-aada-d331dff804c4)


<h1>Quiz 8</h1>

```java
public class nat{
    private String transPort = "203.0.113.55";
    private int portNum = 10000;
    public String get_new_trans(String ip, int port){
        String translated;
        portNum+=1;
        translated = transPort + portNum;
        return translated;
    }
}
```




<h1>Quiz 9</h1>

```java
public class Matrix {
    private int[][] matrix;

    public Matrix(int[][] a) {
        matrix = a;
    }

    public double[][] averages() {
        double[] rowSums = new double[matrix.length];
        double[] colSums = new double[matrix[0].length];

        for (int row = 0; row < matrix.length; row++) {
            for (int col = 0; col < matrix[row].length; col++) {
                rowSums[row] += matrix[row][col];
                colSums[col] += matrix[row][col];
            }
        }

        for (int row = 0; row < rowSums.length; row++) {
            rowSums[row] /= matrix[0].length;
        }

        for (int col = 0; col < colSums.length; col++) {
            colSums[col] /= matrix.length;
        }

        return new double[][] {rowSums, colSums};
    }
}
```



<h1>Quiz 10</h1>

```java
public class Matrix{
    private int[][] matrix;
    public Matrix(int a){
        matrix = new int[a][a];
    }
    public int[][] scale(int m){
        for(int row = 0; row < matrix.length; row++){
            for(int col = 0; col < matrix[row].length;col++){
                matrix[row][col] = matrix[row][col]*m;
            }
        }
        return matrix;
    }
}
```

<h1>Quiz 11</h1>

```java
public class Matrix{
    private int matrix;
    public Matrix(int a){
        matrix = a;
    }
    public int[][] identify(){
        int[][] total = new int[matrix][matrix];
        for(int row = 0; row < total.length; row++){
            for(int col = 0; col < total[row].length;col++){
                if(row == col){
                    total[row][col] = 1;
                }
            }
        }
        return total;
    }
}
```




<h1>Quiz 12</h1>

```java
public int[] vectorize(){
    int length = matrix.length * matrix[0].length;
    int[] vector = new int[length];
    int position = 0;
    for(int i = 0;i<matrix.length;i++){
        for(int x = 0;x<matrix.length;x++){
            matrix[i][x]=vector[position];
            position++;
        }
    }
    return vector;
}
```




<h1>Quiz 13/h1>

```java
public class Matrix{
    private int[] matrix;
    public Matrix(int[] a){
        matrix = a;
    }
    public int[][] toMatrix(){
        int size = (int) Math.ceil(Math.sqrt(matrix.length));
        int[][] newMatrix = new int[size][size];
        int position = 0;
        for(int row =0;row<newMatrix.length;row++){
            for(int col=0;col < newMatrix[row].length;col++){
                if(position < matrix.length){
                    newMatrix[row][col] = matrix[position];
                    position++;
                }
            }
        }
        return newMatrix;
    }
```





<h1>Quiz 14/h1>

```java
public class Matrix{
    private int matrix;
    public Matrix(int a){
        matrix = a;
    }
    public int[][] diagonal(){
        int increment = 0;
        int[][] total = new int[matrix][matrix];
        for(int row = 0; row < total.length; row++){
            for(int col = 0; col < total[row].length;col++){
                if(row == col){
                    total[row][col] = increment;
                    increment++;
                }
            }
        }
        return total;
    }
}
```





<h1>Quiz 15/h1>

```java
public class ADC{
    private double perbit;
    public double calculateADCerror(double sample){
        perbit = (double) 5/Math.pow(2, 6);
        return sample % perbit;

    }
}
```





<h1>Quiz 16/h1>

```java
public class ADC{
    public static int calculateResolution(double minVoltage, double maxVoltage, double[] readings) {
        double smallestDifference = Double.MAX_VALUE;

        for (int i = 0; i < readings.length; i++) {
            for (int x = i + 1; x < readings.length; x++) {
                double difference = Math.abs(readings[i] - readings[x]);

                if (difference > 0 && difference < smallestDifference) {
                    smallestDifference = difference;
                }
            }
        }

        double requiredLevels = (maxVoltage - minVoltage) / smallestDifference;
        int bits = 0;

        while (Math.pow(2, bits) < requiredLevels) {
            bits++;
        }

        return bits;
    }
}
```





