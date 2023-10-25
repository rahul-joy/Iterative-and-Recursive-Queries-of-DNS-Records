# Iterative-and-Recursive-Queries-of-DNS-Records


/*
 * Author: RI Rahul
 */
package rahul;

import java.util.ArrayList;
import java.util.List;
class rahul2{
    private String domain;
    private String ipAddress;
    public rahul2(String domain, String ipAddress){
        this.domain=domain;
        this.ipAddress=ipAddress;
    }
        public String getDomain(){
        return domain;
    }
        public String getIpAddress(){
        return ipAddress;
    }
}
class IterativeDNSQuery {
    private List<rahul2> rahul;
        public IterativeDNSQuery(){
        rahul = new ArrayList<>();
        rahul.add(new rahul2("example.com", "93.184.216.34"));
        rahul.add(new rahul2("example.org", "2606:2800:220:1:248:1893:25c8:1946"));
          }
    public String findIpAddress(String domain) {
        for (rahul2 record : rahul) {
            if (record.getDomain().equals(domain)){
                return record.getIpAddress();
            }
        }
        return "not found";
         }
    public static void main(String[] args) {
    IterativeDNSQuery query = new IterativeDNSQuery();
    System.out.println("example.com: " + query.findIpAddress("example.com"));
    System.out.println("example.org: " + query.findIpAddress("example.org"));
    }
}

public class RecursiveDNSQuery{
    private rahul2[] rahul;
    public RecursiveDNSQuery(){
        rahul=new rahul2[2];
        rahul[0]=new rahul2("example.com", "93.184.216.34");
        rahul[1]=new rahul2("example.org", "2606:2800:220:1:248:1893:25c8:1946");     
    }
    public String findIpAddress(String domain, int index){
        if (index >= rahul.length) {
            return "Not found";
        }
        if (rahul[index].getDomain().equals(domain)){
            return rahul[index].getIpAddress();
        }
        return findIpAddress(domain, index + 1);
    }
    public static void main(String[] args) {
    RecursiveDNSQuery query = new RecursiveDNSQuery();
    System.out.println("example.com: " + query.findIpAddress("example.com",0));
    System.out.println("example.org: " + query.findIpAddress("example.org",0));
    }
}
