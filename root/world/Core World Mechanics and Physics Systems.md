# Economic Systems

## Currency System
### Base Currency
```yaml
Standard Units:
  Gold Crown (GC):
    Value: Base unit
    Weight: 10g
    Magic Content: 0.1%

  Silver Mark (SM):
    Value: 0.01 GC
    Weight: 5g
    Magic Content: 0.05%

  Copper Piece (CP):
    Value: 0.001 GC
    Weight: 2g
    Magic Content: 0.01%

Magical Currency:
  Mana Crystal (MC):
    Value: Variable (1-1000 GC)
    Weight: 1g per power level
    Magic Content: 10-100%
```

### Currency Exchange
```python
def calculate_exchange_rate(currency_a, currency_b, location):
    base_rate = CURRENCY_RATES[currency_a][currency_b]
    magic_modifier = location.magic_density / STANDARD_MAGIC_DENSITY
    political_modifier = get_political_factors(location)
    
    return base_rate * magic_modifier * political_modifier
```

## Market System
### Price Calculation
```python
class MarketSystem:
    def calculate_price(self, item, location, time):
        base_price = item.base_value
        demand_modifier = self.get_demand(item, location, time)
        supply_modifier = self.get_supply(item, location, time)
        magic_modifier = location.magic_density_factor
        
        final_price = (
            base_price 
            * demand_modifier 
            * supply_modifier 
            * magic_modifier
            * location.tax_rate
        )
```

### Trade Routes
```yaml
Route Types:
  Land Routes:
    Risk Factor: 1.2
    Time Multiplier: 1.0
    Cost per Distance: 0.001 GC/km

  Sea Routes:
    Risk Factor: 1.5
    Time Multiplier: 0.8
    Cost per Distance: 0.0005 GC/km

  Magical Routes:
    Risk Factor: 2.0
    Time Multiplier: 0.1
    Cost per Distance: 0.01 GC/km
```

## Resource Economy
### Resource Value
```python
def calculate_resource_value(resource, quality, location):
    base_value = RESOURCE_BASE_VALUES[resource.type]
    quality_modifier = quality ** 1.5
    rarity_factor = 1 + (1 - resource.abundance)
    magic_utility = resource.magic_content * location.magic_demand
    
    return base_value * quality_modifier * rarity_factor * magic_utility
```

### Production Chains
```yaml
Production Steps:
  Raw Materials:
    Value Modifier: 1.0
    Processing Time: None
    Skill Required: None

  Refined Materials:
    Value Modifier: 2.0
    Processing Time: 1-10 days
    Skill Required: Novice

  Crafted Items:
    Value Modifier: 5.0
    Processing Time: 2-20 days
    Skill Required: Adept

  Magical Items:
    Value Modifier: 10.0+
    Processing Time: 5-50 days
    Skill Required: Expert
```

## Service Economy
### Skill-Based Pricing
```python
def calculate_service_cost(service, provider, location):
    base_cost = SERVICE_BASE_COSTS[service.type]
    skill_modifier = 1 + (provider.skill_level / 100)
    reputation_modifier = 1 + (provider.reputation / 50)
    demand_modifier = location.get_service_demand(service.type)
    
    return base_cost * skill_modifier * reputation_modifier * demand_modifier
```

### Quest Economy
```yaml
Quest Rewards:
  Difficulty Levels:
    Easy:
      Base Reward: 10 GC
      Risk Factor: 1.1
      Time Estimate: 1 day

    Medium:
      Base Reward: 100 GC
      Risk Factor: 1.5
      Time Estimate: 1 week

    Hard:
      Base Reward: 1000 GC
      Risk Factor: 2.0
      Time Estimate: 1 month

    Legendary:
      Base Reward: 10000+ GC
      Risk Factor: 5.0
      Time Estimate: Variable
```

## Economic Balance
### Inflation Control
```python
def adjust_economy(world_state):
    total_currency = world_state.get_total_currency()
    total_value = world_state.get_total_goods_value()
    
    inflation_rate = (total_currency / total_value) - 1
    
    if inflation_rate > 0.1:
        implement_currency_sinks()
    elif inflation_rate < -0.1:
        implement_currency_sources()
```

### Market Stability
```yaml
Stability Factors:
  Supply Control:
    - Resource Spawn Rates
    - Production Capacities
    - Import/Export Limits

  Demand Control:
    - Population Needs
    - Quest Generation
    - NPC Wealth Distribution

  Price Control:
    - Minimum Prices
    - Maximum Prices
    - Price Fluctuation Limits
```

