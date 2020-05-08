FROM alpine/git as clone
WORKDIR /usr/src
RUN git clone https://github.com/Bibek-Sutradhar/HotelService.git


FROM maven:3.5-jdk-8-alpine as build
WORKDIR /app
COPY --from=clone /usr/src/HotelService/HotelService /app
RUN mvn install


FROM openjdk:8-jre-alpine
WORKDIR /app
EXPOSE 8888
COPY --from=build /app/target/hotelService-1.0.jar /app
CMD ["java", "-jar", "hotelService-1.0.jar"]
