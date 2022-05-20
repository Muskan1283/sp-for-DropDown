# sp-for-DropDown


create database MVC_ADO
use MVC_ADO

create table Country
(id int primary key identity,
Name Varchar(80))

create table State
(id int primary key identity,
Name Varchar(80),
Countryid int foreign Key references Country(id))

create table City
(id int primary key identity,
Name Varchar(80),
Stateid int foreign Key References State(id))

insert into Country values('India'),('USA'),('Japan'),('Rusiya'),('Pakistan')

insert into State values
('Delhi',1),
('Mumbai',1),
('Up',1),
('Tokyo',3),
('Hirosima',2)

insert into City values
('Gaziabad',3),
('Noida',3),
('South Ex',1)

select*from Country
select*from State
select*from City


Create proc sp_get_Country
as
begin
select id,Name from Country
end

Create proc sp_get_State
@id int 
as
begin
select id,Name from State where Countryid=@id
end

Create proc sp_get_City
@id int 
as
begin
select id,Name from City where Stateid=@id
end

sp_get_State 2
 sp_get_City 3
