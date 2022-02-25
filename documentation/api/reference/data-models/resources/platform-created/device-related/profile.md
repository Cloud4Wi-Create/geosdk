* [Documentation Home](../../../../../../README.md)  
  * [Web API](../../../../../index.md)  
    * [Reference](../../../../index.md)
        * [Data models](../../../index.md)
		    * [Resources Data models](../../index.md)
                * [Platform-created Resources Data models](../index.md)
                    * [Device-related Resources Data models](index.md)

# UserProfile

Data Model used to represent a [*UserProfile*](../../../../resources/platform-created/device-related/profile.md) Resource.

## Fields Specificcation

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](../../../common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers
student  | `Number` | Any number in [0,1] |
parentWithKids  | `Number` | Any number in [0,1] |
groceryShopper  | `Number` | Any number in [0,1] |
luxuryShopper  | `Number` | Any number in [0,1] |
cinemaAddict  | `Number` | Any number in [0,1] |
frequentFlyer  | `Number` | Any number in [0,1] |
trainTraveller  | `Number` | Any number in [0,1] |
carOwner  | `Number` | Any number in [0,1] |
carBuyer  | `Number` | Any number in [0,1] |
consumerElectronicBuyer  | `Number` | Any number in [0,1] |
shoesLover  | `Number` | Any number in [0,1] |
jewelleryAndLuxuryWatchBuyer  | `Number` | Any number in [0,1] |
bankVisitor  | `Number` | Any number in [0,1] |
golfPlayer  | `Number` | Any number in [0,1] |
tennisPlayer  | `Number` | Any number in [0,1] |
footballFan  | `Number` | Any number in [0,1] |
artsAndCultureEnthusiast  | `Number` | Any number in [0,1] |
musicAndNightLifeLover  | `Number` | Any number in [0,1] |
diyLover  | `Number` | Any number in [0,1] |
petOwner  | `Number` | Any number in [0,1] |
fastFoodLover  | `Number` | Any number in [0,1] |
foodie  | `Number` | Any number in [0,1] |
beautyAndWellnessEnthusiast  | `Number` | Any number in [0,1] |
shoppingLover  | `Number` | Any number in [0,1] |
healthAndFitnessEnthusiast  | `Number` | Any number in [0,1] |
bookLover  | `Number` | Any number in [0,1] |
theaterLover  | `Number` | Any number in [0,1] |
carEnthusiast  | `Number` | Any number in [0,1] |
atWorkEarly  | `Number` | Any number in [0,1] |
averageCommuter  | `Number` | Any number in [0,1] |
businessTraveller  | `Number` | Any number in [0,1] |
employed  | `Number` | Any number in [0,1] |
leavingWorkLate  | `Number` | Any number in [0,1] |
longCommuter  | `Number` | Any number in [0,1] |
partTimeWorker  | `Number` | Any number in [0,1] |
unemployed  | `Number` | Any number in [0,1] |
weekendAtHome  | `Number` | Any number in [0,1] |
weekendAway  | `Number` | Any number in [0,1] |
weekendWorker  | `Number` | Any number in [0,1] |
workaholic  | `Number` | Any number in [0,1] |
incomeLow  | `Number` | Any number in [0,1] |
incomeMedium  | `Number` | Any number in [0,1] |
incomeHigh  | `Number` | Any number in [0,1] |
educationLevelLow  | `Number` | Any number in [0,1] |
educationLevelMedium  | `Number` | Any number in [0,1] |
educationLevelHigh  | `Number` | Any number in [0,1] |
familySizeSmall  | `Number` | Any number in [0,1] |
familySizeMedium  | `Number` | Any number in [0,1] |
familySizeLarge  | `Number` | Any number in [0,1] |
houseValueLow  | `Number` | Any number in [0,1] |
houseValueMedium  | `Number` | Any number in [0,1] |
houseValueHigh  | `Number` | Any number in [0,1] |
highExpenditureClothing  | `Number` | Any number in [0,1] |
highExpenditureHotelAndRestaurants  | `Number` | Any number in [0,1] |
highExpenditureCommunication  | `Number` | Any number in [0,1] |
highExpenditurePersonalCare  | `Number` | Any number in [0,1] |
highExpenditureHomeAppliances  | `Number` | Any number in [0,1] |
highExpenditureElectricityAndGas  | `Number` | Any number in [0,1] |
highExpenditureEducation  | `Number` | Any number in [0,1] |
highExpenditureVacationPackages  | `Number` | Any number in [0,1] |
highExpenditurePersonalVehicle  | `Number` | Any number in [0,1] |
highExpenditurePensionFundAndLifeInsurance  | `Number` | Any number in [0,1] |
highPropensityToDebts  | `Number` | Any number in [0,1] |
highPropensityToInvestments  | `Number` | Any number in [0,1] |
highPropensityToPersonalLoans  | `Number` | Any number in [0,1] |
highPropensityToSavings  | `Number` | Any number in [0,1] |
highPropensityToHouseLoan  | `Number` | Any number in [0,1] |
highPropensityToOnlinePurchase  | `Number` | Any number in [0,1] |


## Example Object

```json
{
	"device": {
		"id": "57cb076c62843f000110d406",
		"clientAppId": "57b2fa2de0ee4400011480f1",
		"customId": "my device",
		"idfa": "6f942f09-4f5e-474d-8a94-3ee197312c38"
	},
	"student": 0,
	"parentWithKids": 0.5,
	"groceryShopper": 0.5,
	"luxuryShopper": 0,
	"cinemaAddict": 0,
	"frequentFlyer": 0,
	"trainTraveller": 0,
	"carOwner": 0.8333333333333333,
	"carBuyer": 1,
	"consumerElectronicBuyer": 1,
	"shoesLover": 0,
	"jewelleryAndLuxuryWatchBuyer": 0,
	"bankVisitor": 0,
	"golfPlayer": 1,
	"tennisPlayer": 1,
	"footballFan": 1,
	"artsAndCultureEnthusiast": 1,
	"musicAndNightLifeLover": 1,
	"diyLover": 1,
	"petOwner": 1,
	"fastFoodLover": 1,
	"foodie": 1,
	"beautyAndWellnessEnthusiast": 1,
	"shoppingLover": 0.5,
	"healthAndFitnessEnthusiast": 0.5,
	"bookLover": 1,
	"theaterLover": 1,
	"carEnthusiast": 0,
	"atWorkEarly": 1,
	"averageCommuter": 1,
	"businessTraveller": 0,
	"employed": 1,
	"leavingWorkLate": 0,
	"longCommuter": 0,
	"partTimeWorker": 1,
	"unemployed": 1,
	"weekendAtHome": 1,
	"weekendAway": 0,
	"weekendWorker": 1,
	"workaholic": 1,
	"incomeLow": 0,
	"incomeMedium": 0,
	"incomeHigh": 1,
	"educationLevelLow": 1,
	"educationLevelMedium": 0,
	"educationLevelHigh": 0,
	"familySizeSmall": 1,
	"familySizeMedium": 0,
	"familySizeLarge": 1,
	"houseValueLow": 0,
	"houseValueMedium": 0,
	"houseValueHigh": 1,
	"highExpenditureClothing": 1,
	"highExpenditureHotelAndRestaurants": 0,
	"highExpenditureCommunication": 1,
	"highExpenditurePersonalCare": 1,
	"highExpenditureHomeAppliances": 1,
	"highExpenditureElectricityAndGas": 0,
	"highExpenditureEducation": 1,
	"highExpenditureVacationPackages": 1,
	"highExpenditurePersonalVehicle": 1,
	"highExpenditurePensionFundAndLifeInsurance": 1,
	"highPropensityToDebts": 1,
	"highPropensityToInvestments": 1,
	"highPropensityToPersonalLoans": 1,
	"highPropensityToSavings": 1,
	"highPropensityToHouseLoan": 1,
	"highPropensityToOnlinePurchase": 0
}
```
