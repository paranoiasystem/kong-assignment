# CURL Tests

## Flights Service

```bash
# Get all flights
curl http://localhost:8000/api/v1/flights | jq

# Get a specific flight by number
curl http://localhost:8000/api/v1/flights/KA0284 | jq

# Get flight details
curl http://localhost:8000/api/v1/flights/KA0284/details | jq

# Health check
curl http://localhost:8000/api/v1/flights/health | jq
```

## Bookings Service

```bash
# Get bookings for a customer
curl -H "X-Consumer-Username: jdoe" http://localhost:8000/api/v1/bookings | jq

# Create a new booking
curl -X POST -H "Content-Type: application/json" -H "X-Consumer-Username: jdoe" \
  -d '{"flight_number":"KA0284","seat":"12A"}' \
  http://localhost:8000/api/v1/bookings | jq

# Health check
curl http://localhost:8000/api/v1/bookings/health | jq
```

## Customer Service

```bash
# Get customer information
curl -H "X-Consumer-Username: jdoe" http://localhost:8000/api/v1/customer | jq

# Health check
curl http://localhost:8000/api/v1/customer/health | jq
```

## Routes Service

```bash
# Get all routes
curl http://localhost:8000/api/v1/routes | jq

# Get a specific route by id
curl http://localhost:8000/api/v1/routes/LHR-SFO | jq

# Health check
curl http://localhost:8000/api/v1/routes/health | jq
```