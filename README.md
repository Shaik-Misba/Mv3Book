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
	 <b> if(isvalidCustomerPhoneNo(movieBookDTO.getCustomerPhoneNo())==false){
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
	public interface MovieBookingRepository extends CrudRepository <*MovieBooking,Integer*>
	{
	@Query("select m from MovieBooking m where m.customerPhoneNo=:customerPhoneNo and m.showDate=:showDate")
	List<*MovieBooking*> getBookingDetails(Long customerPhoneNo, LocalDate showDate);
	List<*MovieBooking*> findByScreenName(String screenName);
	}
</code></p>
 
 **MovieBookingServiceImpl.java---->**

<p><code><b>@Service(value="movieBookingService")
@Transactional</b>
public class MovieBookingServiceImpl implemnts 
{
	<b>@Autowired</b>
	private MovieBookingRepository movieBookingRepository;
	
	@Override 
        public List<MovieBookingDTO> getBookingByScreenName(String screenName) throws MovieBookingException {
	List<MovieBooking> list= movieBookRepository.findByScreenName(screenName);
      		if(list.isEmpty()){
			throw new MovieBookingException("MovieBookingService.NO_BOOKING");
   		}
     		List<MovieBookingDTO> dtoList = new ArrayList<>();
       		for(MovieBooking movieBooking : list){
	           MovieBookingDTO dto =MovieBookingDTO.prepareDTO(movieBooking);
	           dtoList.add(dto);
	        }
	        return dtoList;
	 }
 
 
 }
 </code></p>

** MovieBookingAPI.java-->**

