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




<h1>Quiz 13</h1>

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





<h1>Quiz 14</h1>

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





<h1>Quiz 15</h1>

```java
public class ADC{
    private double perbit;
    public double calculateADCerror(double sample){
        perbit = (double) 5/Math.pow(2, 6);
        return sample % perbit;

    }
}
```





<h1>Quiz 16</h1>

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


<h1>Proofs</h1>
<img width="1440" height="900" alt="Screenshot 2026-10-16 at 11 34 41" src="https://github.com/user-attachments/assets/a65e55ef-002a-4110-af12-ddf7c2dcaa6a" />
<img width="1440" height="900" alt="Screenshot 2026-10-16 at 11 34 45" src="https://github.com/user-attachments/assets/0d68fcfc-e3a7-4de6-aabf-9f3fa5692988" />
<img width="1440" height="900" alt="Screenshot 2026-10-16 at 11 34 54" src="https://github.com/user-attachments/assets/dc9ae4c7-e8c6-479e-bbf7-9e13ce412cc1" />


<h1>Quiz 17</h1>
Encapsulation is the process of adding specific headers for each protocol to data as it moves across the TCP/IP model. Each layer has its own information, allowing the device to transfer data.

<h1>Quiz 18</h1>
Tunneling: Creating secure connections through existing networks
Encryption: Making data unreadable to outside parties
Authentication: Verifying user identity

<h1>Quiz 19</h1>
HTTP or Hyper Text Transfer Protocol. HTTP is used to transfer web pages between the client and the server. 

<h1>Quiz 20</h1>
Missing value handling. This is when you find records that contain missing data and either remove or fill in those entries. 

<h1>Quiz 21</h1>
Some customers could leave questions blank and unanswered. This incompletet data would then need to go through data preprocessing to make sure that the algorithm runs into no missing data errors by either removing or filling in the unanswered category. For example, missing numerical responses could be replaced with the mean or median of the available responses. This allows the model to work with a more complete and consistent dataset.

<h1>Quiz 22</h1>
Firstly, data preprocessing allows for the training data to be accurate for the machine learning model. You can remove or fill in missing data. You can normalize the data to specific ranges in order to prevent a disproportional influence in features, such as exam scores or attedance. You can also remove repeated or false data. This helps remove the chance of incorrect patterns observered in the model. Finally, irrelevant features can be removed through feature selection, reducing unnecessary complexity and helping the model focus on the most important factors influencing student performance.

<h1>Quiz 23</h1>
A university could use a wrapper method to reduce the dimensionality of its dataset by testing different combinations of the 50 applicant metrics. The wrapper method would repeatedly train and evaluate an ML model using different subsets of features to determine which combination produces the best predictive performance. For example, it might discover that academic grades, attendance and extracurricular involvement are more useful predictors than some other metrics. Irrelevant or redundant features can then be removed, reducing the number of dimensions in the dataset. This decreases computational complexity and training time while potentially reducing overfitting.

<h1>Quiz 24</h1>
It is used to determine how well the model generalizes unseen data. The dataset is divided into K equally sized folds. The model is trained on K−1 folds and tested on the remaining fold. This process is repeated K times, with a different fold used for testing each time. The performance results are then averaged to produce a more reliable estimate of the model's accuracy.
