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












