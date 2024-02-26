# MovieBookingServiceImpl.java---->

Public Double calculateBookingmount(Integer noOfSeats,Strong screenName){
	double bookinfAmount=0.0;
	if(screenName.equals("Rhombus")){
		bookingAmount=100.0*noOfSeats;
	} else if(screenName.equals("Sapphire")){
		bookingAmount=200.0*noOfseats;
	}else{
		booningAmount=300.0*noOfSeats;
	}
	return bookingAmount;
 }
 
