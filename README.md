# abas-interview-questions
ABAS Interview Questions


public void answers() {

    List<Orders> orders = new ArrayList<>();

    orders.add(new Orders(1000, 2000, 12, 100.51));
    orders.add(new Orders(1000, 2001, 31, 200));
    orders.add(new Orders(1000, 2002, 22, 150.86));
    orders.add(new Orders(1000, 2003, 41, 250));
    orders.add(new Orders(1000, 2004, 55, 244));
    orders.add(new Orders(1001, 2001, 88, 44.531));
    orders.add(new Orders(1001, 2002, 121, 88.11));
    orders.add(new Orders(1001, 2004, 74, 211));
    orders.add(new Orders(1001, 2002, 14, 88.11));
    orders.add(new Orders(1002, 2003, 2, 12.1));
    orders.add(new Orders(1002, 2004, 3, 22.3));
    orders.add(new Orders(1002, 2003, 8, 12.1));
    orders.add(new Orders(1002, 2002, 16, 94));
    orders.add(new Orders(1002, 2005, 9, 44.1));
    orders.add(new Orders(1002, 2006, 19, 90));

    double total = orders.stream().mapToDouble(Orders::getTotalPrice).sum();
    double averagePrice = orders.stream().mapToDouble(Orders::getUnitPrice).average().orElse(0);

    Map<Integer, Double> averagePricePerItem = orders.stream()
        .collect(Collectors.groupingBy(Orders::getItemNumber,
            Collectors.averagingDouble(Orders::getUnitPrice)));

    Map<Integer, Map<Integer, Long>> itemOrderCount = orders.stream()
        .collect(Collectors.groupingBy(Orders::getItemNumber,
            Collectors.groupingBy(Orders::getOrderNumber,
                Collectors.summingLong(Orders::getQuantity))));

    System.out.println("Toplam Tutar: " + total);
    System.out.println("Bütün malların ortalama fiyatı: " + averagePrice);

    averagePricePerItem.forEach((itemNumber, avgPrice) ->
        System.out.println("Mal Numarası: " + itemNumber + " Ortalama Fiyat: " + avgPrice + "\n"));

    itemOrderCount.forEach((itemNumber, orderMap) -> {
      System.out.println("Mal Numarası: " + itemNumber);
      orderMap.forEach((orderNumber, quantity) ->
          System.out.println("Sipariş Numarası: " + orderNumber + " Adet: " + quantity));
    });

  }
Kodların çıktıları : 

<img width="804" alt="image" src="https://github.com/user-attachments/assets/c5f4c898-a5eb-4bcb-9e58-0a80b23bc06a">


Post ve Get Request ve Response Örneği : 

Aşağıda belirttiğim github linkinden daha önce hazırladığım bir projenin README dosyasından daha detaylı isteklere ulaşabilirsiniz. 
Mevcutta atılan bir POST isteğinin body'si ve response'u aşağıda mevcuttur.

https://github.com/zaf012/eva-exchange-api/blob/main/README.md

<img width="1082" alt="image" src="https://github.com/user-attachments/assets/3287d987-635a-4842-b349-ea4d58be8f06">




