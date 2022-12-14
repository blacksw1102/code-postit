# enum을 활용한 클래스 필드 상태 값 관리

```java
import java.util.Date;

public class MyClass {
    public static void main(String args[]) {
        Order order = new Order(1000, new Date(), OrderStatus.PENDING_PAYMENT);
        System.out.println(order);
    }
}

enum OrderStatus {
    PENDING_PAYMENT,
    PROCESSING,
    SHIPPED,
    DELIVERED
};

class Order {
    private Integer id;
    private Date moment;
    private OrderStatus status;

    public Order() { }

    public Order(Integer id, Date moment, OrderStatus status) {
		this.id = id;
		this.moment = moment;
		this.status = status;
	}

	public Integer getId() {
		return id;
	}

	public void setId(Integer id) {
		this.id = id;
	}

	public Date getMoment() {
		return moment;
	}

	public void setMoment(Date moment) {
		this.moment = moment;
	}

	public OrderStatus getStatus() {
		return status;
	}

	public void setStatus(OrderStatus status) {
		this.status = status;
	}

	@Override
	public String toString() {
		return "Order [id=" + id + ", moment=" + moment + ", status=" + status + "]";
	}
}
```
