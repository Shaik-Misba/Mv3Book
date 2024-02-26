**DTO-->**
<p><code>//Below bookingid
	<b>@NotNull(message="{bookingmovie.moviename.notpresent}")</b>
	private String movieName;
	<b>@NotNull(message="{bookingmovie.screenname.notpresent}")
	@Pattern(regexp="Sapphire|Turquoise|Rhombus", message=*{bookmovie.screenname.invalid}")</b>
	private String screenName;
	<b>@NotNull(message="{bookingmovie.showdate.notpresent}")
	@FutureOrPresent(message="{bookmovie.showdate.invalid}")</b>
	private LocalDate showDate;
	<b>@NotNull(message="{bookingmovie.noOfSeats.notpresent}")
	@Min(value=1,message="{bookmovie.noOfseats.Invalid}")
	@Max(value=5,message="{bookmovie.noOfseats.Invalid}")</b>
	privare Integer noOfSeats;
</code></p>

**Entity MovieBooking.java-->**
<p><code><b>@Entity
	@Table(name="movie_booking")</b>
	public class MovieBooking{
	<b>	@Id
		@GeneratedValue(strategy=GenerationType.IDENTITY)
	</b>    private Integer bookingId;
	}
</code></p>

**MovieBookingValidator.java-->**
 <p><code>
	 public static void validate(){
	 <b>if(isvalidCustomerPhoneNo(movieBookDTO.getCustomerPhoneNo())==false){
	 throw new MovieBookingException("Validator.INVALID_CUSTOMER_PHONE_NO");
	 }
	 if(isvalidPaymentType(movieBookDTO.getPaymentType()==false){
	 throw new MovieBookingException("Validator.INVALID_PAYMENT_TYPE");
	 }</b>
	 }
	  public static Boolean isValidPaymenType(String paymentType){
	 <b>String regex="Card|Wallet|NetBanking";
	 if(paymentType.matches(regex)){
	 return true;
	 }
	 return false;</b>
	 }
	 public static Boolean isValidCustomerPhoneNo(Long customerPhoneNo){
	 <b>String regex="[3-9]{1}[0-9]{9}";
		 if(customerPhoneNo.toString().matches(regex)){
		 return true;
		 {
		 return false;</b>
	 }
 </code></p>
 
**MovieBookingRepository.java**
<p><code>
	publid interface MovieBookingRepository <b> extends CrudRepository MovieBooking,Integer </b> 
	{
	@Query("select m from MovieBooking m where m.customerPhoneNo=:customerPhoneNo and m.showDate=:showDate")
	List<MovieBooking> 
</code></p>
 
 **MovieBookingServiceImpl.java---->**

<p><code><b>@Service(value="movieBookingService")
@Transactional</b>
public class MovieBookingServiceImpl implemnts 
{
	<b>@Autowired</b>
	private MovieBookingRepository movieBookingRepository;
 	Public Double calculateBookingmount(Integer noOfSeats,Strong screenName){
		<b>double bookinfAmount=0.0;
		if(screenName.equals("Rhombus")){
		bookingAmount=100.0*noOfSeats;
		} else if(screenName.equals("Sapphire")){
		bookingAmount=200.0*noOfseats;
		}else{
		booningAmount=300.0*noOfSeats;
		}
		return bookingAmount;</b>
  	}
	
 }</code></p>

 
