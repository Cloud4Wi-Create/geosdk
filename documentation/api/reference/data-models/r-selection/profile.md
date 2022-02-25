# UserProfile-Segment

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-device-base.md) 
clothingExpenditure|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
hotelAndRestaurantsExpenditure|[ `Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
communicationExpenditure|[ `Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
personalCareExpenditure|[ `Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
homeAppliancesExpenditure|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
electricityAndGasExpenditure|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
educationExpenditure|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
vacationPackagesExpenditure|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
personalVehicleExpenditure|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
income|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
pensionFoundAndLifeInsurance|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
debts|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
unemployed|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
employed|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
investments|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
houseLoan|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
familyMembers|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
onlinePurchases|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
cinema|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
concerts|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
homeBanking|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
museums|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
theatres|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
personalLoans|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
savings|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
educationalQualification|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 
houseValue|[`Point-Integer-SelectionOperation`](/api/reference/data-models/d-c-selection-operation/point-integer.md) 


```json
{
	"deviceBase": { 
		"inside": {
		  	// only one field allowed
			"deviceId": ["D1", "D2", "D3"],
			"applicationId": ["A1", "A2", "A3"],
			"osName": ["android", "iOs"]
		}
	},
	"clothingExpenditure": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"hotelAndRestaurantsExpenditure": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"communicationExpenditure": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"personalCareExpenditure": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"homeAppliancesExpenditure": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"electricityAndGasExpenditure": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"educationExpenditure": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"vacationPackagesExpenditure": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"personalVehicleExpenditure": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"income": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"pensionFoundAndLifeInsurance": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"debts": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"unemployed": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"employed": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"investments": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"houseLoan": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"familyMembers": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"onlinePurchases": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"cinema": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"concerts": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"homeBanking": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"museums": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"theatres": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"personalLoans": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"savings": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"educationalQualification": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 1,
				"to": 2
			}]
		}
	},
	"houseValue": {
		"inside": {
			"values": [0, 1],
			"intervals": [{
				"from": 3,
				"to": 5
			}]
		}
	}
}
```

