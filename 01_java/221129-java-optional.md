```java
@Test
public void givenNonNull_whenCreatesNonNullable() {
	String name = "saelobi";
	Optional<String> opt = Optional.of(name);
	assertEquals("Optional[saelobi]", opt.toString());
}

@Test
public void givenNonNull_whenCreatesNullable() {
	String name = "saelobi";
	Optional<String> opt = Optional.ofNullable(name);
	assertEquals("Optional[saelobi]", opt.toString());
}

@Test
public void givenNull_whenCreatesNullable() {
	String name = null;
	Optional<String> opt = Optional.ofNullable(name);
	assertEquals("Optional.empty", opt.toString());
}

@Test
public void givenOptional_whenIsPresentWorks() {
	Optional<String> opt = Optional.of("saelobi");
	assertTrue(opt.isPresent());

	opt = Optional.ofNullable(null);
	assertFalse(opt.isPresent());
}

@Test
public void givenOptional_whenIfPresentWorks() {
	Optional<String> opt = Optional.of("saelobi");
	opt.ifPresent(name -> System.out.println(name.length()));
}

@Test
public void whenOrElseWorks() {
	String nullName = null;
	String name = Optional.ofNullable(nullName).orElse("John");
	assertEquals("John", name);
}

@Test
public void whenOrElseGetAndElseOverLap() {
	String text = null;
	String defaultText = Optional.ofNullable(text).orElse(getMyDefault());
	assertEquals("Default Value", defaultText);
}

@Test
public void whenOrElseGetAndOrElseDiff() {
	String text = "TEST";
	String defaultText = Optional.ofNullable(text).orElseGet(this::getMyDefault);
	assertEquals("TEST", defaultText);

	defaultText = Optional.ofNullable(text).orElse(getMyDefault());
	assertEquals("TEST", defaultText);
}

@Test(expected = IllegalArgumentException.class)
public void whenOrElseWorks() {
	String nullName = null;
	String name = 	Optional.ofNullable(nullName).orElseThrow(IllegalArgumentException::new);
}

@Test(expected = NoSuchElementException.class)
public void givenOptionalWithNull_whenGetThrowsException() {
	Optional<String> opt = Optional.ofNullable(null);
	String name = opt.get();
}

public boolean priceIsInRange(Modem modem) {
	boolean isInRange = false;
	if (modem != null && modem.getPrice() != null 
		&& (model.getPrice() >= 10 && modem.getPrice() <= 15)) {
		isInRange = true;
	}
	
	return isInRange;
}

public boolean priceIsInRange2(Modem modem) {
	return Optional.ofNullable(modem)
				.map(Modem::getPrice)
				.filter(p -> p >= 10)
				.filter(p -> p <= 15)
				.isPresent();
}

@Test
public void whenFilterWithoutOptional() {
    assertTrue(priceIsInRange2(new Modem(10.0)));
    assertTrue(priceIsInRange2(new Modem(null)));
    assertTrue(priceIsInRange2(new Modem(15.2)));
    assertTrue(priceIsInRange2(null));
}

@Test
public void givenOptional_whenMapWorks() {
	List<String> companyNames = Arrays.asList("Samsung", "SK", "NAVER", "Daum");
	Optional<List<String>> listOptional= Optinal.of(companyNames);
	int size = listOptional.map(List::size).orElse(0);
	assertEquals(4, size);
}

@Test
public void givenOptional_whenMapWorks2() {
	String name = "saelobi";
	Optional<String> nameOptional = Optional.ofNullable(name);
	int len = nameOptional.map(String::length).orElse(0);
	assertEquals(7, len);
}

@Test
public void givenOptional_whenMapWorksWithFilter() {
	String password = "password";
	Optional<String> passOpt = Optional.of(password);
	boolean correctPassword = passOpt
        				.filter(pass -> pass.equals("password"))
						.isPresent();
	assertFalse(correctPassword);

	correctPassword = passOpt.map(String::trim)
						.filter(pass -> pass.equals("password"))
						.isPresent();
	asswertTrue(correctPassword);
}
```