# Open Tracker

*A complete service for opt-in shared live tracking of an entity's GPS location (or any data actually)*

**The code has been moved to a private repo: https://bitbucket.org/iwoodfordteam/open-tracker**


## API

* **socket `connect`**   
  returns an `update_key` *(keep this private, it identifies you)*   
  and a `share_key` *(share this to anything you want to be able to track your updates)*    
  Pass in an existing `update_key` if you have one (and can also pass `meta`)   
  
* **emit `move`**     
  pass in any `data` packet you want to share,     
  but probably a location object like this

```javascript		
    {
		coords.latitude
		coords.longitude
		coords.altitude
		coords.accuracy
		coords.altitudeAccuracy
		coords.heading
		coords.speed
		timestamp
	}
```

* **emit `start_watching`**    
  pass in an other's `share_key`    
  now you receive updates whenever the other moves
  
  
* **on `something_moved`**    
  receive a update of something moving/changing    
  the packet looks like this    
  
```javascript
	{
		share_key : "of whatever moved",
		meta      : { whatever: "meta info they have", name: "for example" },
		data      : { again: "anything", but: "probably a geo location object" }
	}
```

## Design Goals and Ethos

Open Tracker is designed to be :

* simple
* flexible
* secure
* annonomous 

No data is kept about the client using the service other than what it sends in the `meta` or `data` information


## Pricing

The plan is to have the public Open free (see sample projects) for anyone, but data will be flushed periodically.  
A private Open Tracker server can be setup for $50 / month for up to 10,000 updates per month, or up to 1 million updates per month for $500 / month.

