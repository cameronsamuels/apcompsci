## Address.java - Class

```java
public class Address
{
  
  // Variables
  private String streetAddress;
  private String city;
  private String state;
  private String zipCode;
  
  // Constructors
  public Address(String streetAddress, String city, String state, String zipCode) 
  {
    this.streetAddress = streetAddress;
    this.city = city;
    this.state = state;
    this.zipCode = zipCode;
  }
  
  // Accessors
  public String getStreetAddress() { return streetAddress; }
  public String getCity() { return city; }
  public String getState() { return state; }
  public String getZipCode() { return zipCode; }
  
  // Modifiers
  public void setStreetAddress(String x) { streetAddress = x; }
  public void setCity(String x) { city = x; }
  public void setState(String x) { state = x; }
  public void setZipCode(String x) { zipCode = x; }
  
  // toString
  public String toString()
  { return getStreetAddress() + ", " + getCity() + ", " + getState() + " " + getZipCode(); }
  
}
```

**Purpose**
<br>Each instance of an `Address` stores the street address, city, state, and zip code of a physical address.
