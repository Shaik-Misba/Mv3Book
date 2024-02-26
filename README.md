**MovieBookingServiceImpl.java---->**

<p><code><b>@Service(value="movieBookingService")
@Transactional</b>
public class MovieBookingServiceImpl implemnts 
{
	<b>@Autowired</b>
	private MovieBookingRepository movieBookingRepository;
 }</code></p>

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
	@NotNull(message="{bookingmovie.screenname.notpresent}")
	@Pattern(regexp="Sapphire|Turquoise|Rhombus", message=*{bookmovie.screenname.invalid}")</b>
</code></p>
 
