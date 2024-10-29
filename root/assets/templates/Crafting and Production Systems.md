# Crafting Systems

## Base Crafting Mechanics
### Skill Progression
```python
class CraftingSkill:
    def calculate_progress(self, action, difficulty):
        base_exp = difficulty * action.complexity
        intelligence_bonus = (self.intelligence - 10) * 0.05
        talent_modifier = self.crafting_talents.get_modifier()
        
        experience_gain = (
            base_exp 
            * (1 + intelligence_bonus)
            * talent_modifier 
            * self.focus_modifier
        )
        
        return {
            'exp_gained': experience_gain,
            'skill_progress': min(1.0, experience_gain / self.next_level_req),
            'mastery_gain': experience_gain * self.mastery_rate
        }
```

### Quality Calculation
```yaml
Quality Factors:
  Base Quality:
    Materials: 40%
    Skill Level: 30%
    Tools: 20%
    Environment: 10%

  Modifiers:
    Critical Success: ×1.5
    Perfect Materials: ×1.25
    Magical Enhancement: ×1.0-2.0
    Workshop Bonus: ×1.1-1.3

  Special Conditions:
    Divine Blessing: ×1.5-3.0
    Curse Effect: ×0.5-0.8
    Time Pressure: ×0.7-1.3
```

## Crafting Specializations
### Blacksmithing
```python
class BlacksmithingSystem:
    def forge_item(self, materials, blueprint, crafter):
        base_success = self.calculate_base_success(materials, blueprint, crafter)
        heat_management = self.manage_heat_levels(blueprint.required_heat)
        striking_pattern = self.calculate_striking_pattern(blueprint.complexity)
        
        quality_result = (
            base_success.quality
            * heat_management.efficiency
            * striking_pattern.accuracy
        )
        
        special_properties = self.determine_special_properties(
            materials.magical_content,
            crafter.skill_level,
            quality_result
        )
```

### Alchemy
```yaml
Potion Crafting:
  Base Success Rate:
    Novice: 40%
    Adept: 60%
    Expert: 80%
    Master: 95%

  Ingredient Interaction:
    Compatible: +10% quality
    Neutral: +0% quality
    Conflicting: -15% quality
    Catalytic: ×1.5 effect

  Brewing Conditions:
    Temperature Control: ±5% per degree
    Mana Density: ×0.5-2.0 potency
    Moon Phase: ±10% specific effects
    Time of Day: ±5% specific effects
```

### Enchanting
```python
class EnchantingSystem:
    def calculate_enchantment_power(self, item, enchanter, runes):
        base_power = sum(rune.power for rune in runes)
        skill_modifier = 1 + (enchanter.skill_level / 100)
        item_receptivity = item.magic_affinity * item.quality
        
        max_enchant_power = (
            base_power 
            * skill_modifier 
            * item_receptivity 
            * self.magical_atmosphere
        )
        
        stability = self.calculate_stability(
            enchanter.control_rating,
            runes.complexity,
            item.resistance
        )
```

## Material Processing
### Refinement System
```yaml
Processing Methods:
  Physical:
    - Grinding: Powder production
    - Smelting: Metal purification
    - Weaving: Fabric creation
    - Cutting: Gem preparation

  Magical:
    - Mana Infusion: Magic enhancement
    - Element Attunement: Affinity boost
    - Soul Binding: Spirit infusion
    - Reality Anchoring: Stability increase

Quality Improvements:
  Basic: +10% quality
  Advanced: +25% quality
  Master: +50% quality
  Perfect: +100% quality
```

### Material Combination
```python
def combine_materials(material_list, method, crafter):
    base_compatibility = calculate_compatibility(material_list)
    process_efficiency = method.efficiency * crafter.skill_modifier
    
    result_quality = min(
        100,
        sum(m.quality for m in material_list) / len(material_list) 
        * base_compatibility 
        * process_efficiency
    )
    
    special_properties = []
    for material in material_list:
        if random() < (material.special_chance * crafter.luck):
            special_properties.append(material.get_special_property())
```

## Production Management
### Workshop System
```yaml
Workshop Levels:
  Basic:
    Size: 100 sq ft
    Tool Quality: 1.0x
    Storage: 1000 units
    Worker Capacity: 1

  Advanced:
    Size: 250 sq ft
    Tool Quality: 1.2x
    Storage: 2500 units
    Worker Capacity: 3

  Master:
    Size: 500 sq ft
    Tool Quality: 1.5x
    Storage: 5000 units
    Worker Capacity: 5

  Legendary:
    Size: 1000 sq ft
    Tool Quality: 2.0x
    Storage: 10000 units
    Worker Capacity: 10
```

### Production Lines
```python
class ProductionLine:
    def calculate_output(self, recipe, workers, time):
        base_production = recipe.base_output * time.hours
        worker_efficiency = sum(w.efficiency for w in workers)
        workshop_bonus = self.workshop.quality_modifier
        
        total_output = (
            base_production 
            * (worker_efficiency / len(workers))
            * workshop_bonus
            * self.equipment_modifier
        )
        
        quality_variance = calculate_quality_variance(
            workers,
            recipe.complexity,
            self.workshop.conditions
        )
```