Enum
1. 상수와 리터럴을 연결시킬 필요가 없다.
  - 기입된 순서가 인덱스 번호
2. 집합의 네이밍을 명확하게 할 수 있다.
3. 데이터의 변화가 생길 경우 enum만 수정하면 된다.

```java
    public enum PayGroup {
    	CASH("현금", Arrays.asList("ACCOUNT_TRANSFER", "REMITTANCE", "ON_SITE_PAYMENT", "TOSS")),
    	CARD("카드", Arrays.asList("PAYCO", "CARD", "KAKAO_PAY", "BAEMIN_PAY")),
    	ETC("기타", Arrays.asList("POINT", "COUNT")),
    	EMPTY("없음", Collections.emptyList());
    	
    	private String title;
    	private List<String> payList;
    	
    	private PayGroup(String title, List<String> payList) {
    		this.title = title;
    		this.payList = payList;
    	}
    	
    	public static PayGroup findByPayCode(String code){
    	    return 
    	            //PayGroup의 Enum 상수들을 순회하며
    	            Arrays.stream(PayGroup.values())
    	            //payCode를 갖고 있는게 있는지 확인합니다.
    	            .filter(payGroup -> payGroup.hasPayCode(code))
    	            .findAny()
    	            .orElse(EMPTY);
    	}

    	public boolean hasPayCode(String code){
    	    return payList.stream()
    	            .anyMatch(pay -> pay.equals(code));
    	}
    	
        public PayType findPayTypeByPayCode(String payCode) {
            for (PayType type : PayType.values()) {
                if (hasPayCode(payCode)) {
                    return type;
                }
            }
            return PayType.EMPTY; // 찾지 못한 경우 빈 PayType 반환
        }
        
    	public String getTitle() {return title;}
    }
    
    public enum PayType {
    	ACCOUNT_TRANSFER("계좌이체"),
    	REMITTANCE("무통장입금"),
    	ON_SITE_PAYMENT("현장결제"),
    	TOSS("토스"),
    	PAYCO("페이코"),
    	CARD("신용카드"),
    	KAKAO_PAY("카카오페이"),
    	BEAMIN_PAY("배민페이"),
    	POINT("포인트"),
    	COUPON("쿠폰"),
    	EMPTY("없음");
    	
    	private String title;
    	
    	PayType(String title) { this.title = title; }
    	
    	public String getTitle() { return title; }
	}
    
	@Test
    public void paygroupDirectPaySelect () throws Exception {
//    	String payCode = selectPayCode();
//    	String payCode = "BAEMIN_PAY";
    	String payCode = "REMITTANCE";
    	PayGroup payGroup = PayGroup.findByPayCode(payCode);
    	PayType payType = PayType.valueOf(payCode);   	    
    	System.out.println(payGroup.name());
    	System.out.println(payGroup.getTitle());
    	System.out.println(payType.getTitle());
//    	assertThat(payGroup.name(),is("BAEMIN_PAY"));
//    	assertThat(payGroup.getTitle(),is("배민페이"));
    }
```