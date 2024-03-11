create table train( train_number integer(10) primary key, name varchar(20), source
varchar(20),destination varchar(20),start_time timestamp, reach_time datetime,
travel_time datetime, class varchar(20), days varchar(20), distance integer(10),
type varchar(20));

create table ticket( pnr_no char(11) primary key, Transaction_id char(10),
from_station varchar(20), To_station varchar(20), date_of_journey date, class
varchar(10), date_of_booking date, total_ticket_fare integer(5), train_number
integer(10), Foreign key(train_number) references train(train_number));

create table Passenger(pnr_no char(11),Foreign key (pnr_no) references
ticket(pnr_no), serial_no integer(2), name varchar(20), age integer(3),
reservation_status varchar(10), constraint psng_pk primary key(pnr_no, serial_no));

create table TrainRoute(train_no integer(10), constraint tr_fk foreign key (train_no)
references train(train_number), route_no integer (10), station_code char(3), name

varchar(20), arrival_time datetime, depart_time timestamp(0), distance integer(4),
day integer(10), constraint tr_pk primary key(train_no, route_no));

create table train_tkt_Fare(train_no integer(10),constraint tr1_fk foreign
key(train_no) references train(train_no), class varchar(10), base_fare integer(3),
reservation_charge integer(3), superfast_charge integer(3), other_charge integer(3),
tatkal_charge integer(3), service_tax integer(3), constraint tf_pk primary
key(train_no, class));
