```java
package Cropick;

import com.Cropick.Test.WebController;
import org.junit.jupiter.api.Test;
import org.springframework.boot.test.context.SpringBootTest;

import static org.junit.jupiter.api.Assertions.assertEquals;
import static org.junit.jupiter.api.Assertions.assertThrows;


@SpringBootTest(classes = CropickApplicationTests.class)
class CropickApplicationTests {

	@Test
	public void testAdd() {
		assertEquals(42, Integer.sum(19, 23));
	}

	// assertThrows 는 Throws Exception 테스트의 이전 스타일을 대체하는 JUnit5의 새로운 기능이다.
	@Test
	public void testDivide() {
		// ArithmeticException이 발생하는지 확인합니다.
		assertThrows(ArithmeticException.class, () -> {
			Integer.divideUnsigned(42, 0);
		});
	}

	@Test
	public void testEnum () throws Exception {
//    	String payCode = selectPayCode();
    	String payCode = "BAEMIN_PAY";
//		String payCode = "REMITTANCE";
		WebController.PayGroup payGroup = WebController.PayGroup.findByPayCode(payCode);
		WebController.PayType payType = WebController.PayType.valueOf(payCode);

		assertEquals(payType.getTitle(),"배민페이");
    	assertEquals(payGroup.name(),"CARD");
    	assertEquals(payGroup.getTitle(),"카드");
	}
}
```