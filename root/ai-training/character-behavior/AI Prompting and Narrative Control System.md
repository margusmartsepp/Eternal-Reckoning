# AI Prompting System

## Character Voice Generation
### Base Personality Template
```yaml
Character: [Name]
Core Traits:
  - Primary: [Main personality trait]
  - Secondary: [Supporting traits]
  - Flaws: [Character weaknesses]
  
Speech Pattern:
  Vocabulary Level: [1-10]
  Formality: [1-10]
  Complexity: [1-10]
  Dialect: [Specific patterns]
  
Emotional Range:
  - Primary: [Main emotional state]
  - Secondary: [Supporting emotions]
  - Triggers: [What causes emotional shifts]
  
Knowledge Base:
  - Areas of Expertise: [List]
  - Blind Spots: [List]
  - Learning Style: [Description]
```

### Dialogue Generation Rules
```
[Character Name] Response Pattern:
1. Initial Reaction
   {emotional_state} + {personality_filter} + {knowledge_check}

2. Response Formation
   {speech_pattern} + {character_goal} + {current_context}

3. Action Integration
   {physical_response} + {magical_effects} + {environment_interaction}
```

## Scene Construction
### Environment Template
```yaml
Location: [Name]
Atmosphere:
  - Visual Elements: [List]
  - Sounds: [List]
  - Smells: [List]
  - Magical Presence: [Description]

Weather:
  - Current Conditions: [Description]
  - Magical Effects: [List]
  - Impact on Scene: [Description]

Dynamic Elements:
  - Moving Objects: [List]
  - NPC Activities: [List]
  - Background Events: [List]
```

### Scene Flow Control
```python
def generate_scene(tension_level, importance, characters):
    # Pacing Control
    pacing = tension_level * importance
    detail_level = importance * 1.5
    
    # Scene Elements
    required_elements = [
        "setting_description",
        "character_positions",
        "ambient_details",
        "key_focal_points"
    ]
    
    # Dynamic Adjustments
    tension_modifiers = {
        "description_length": pacing * 100,
        "detail_density": detail_level * 0.8,
        "action_frequency": tension_level * 1.2
    }
```

## Narrative Control
### Plot Point Template
```yaml
Event: [Name]
Significance:
  - Plot Impact: [1-10]
  - Character Development: [1-10]
  - World Building: [1-10]

Required Elements:
  - Key Characters: [List]
  - Location: [Description]
  - Time Frame: [Duration]
  - Magical Elements: [List]

Outcome Variations:
  - Primary Path: [Description]
  - Alternate Paths: [List]
  - Failure States: [List]
```

### Causality Chain Management
```python
def generate_consequences(action, significance, time_depth):
    consequences = {
        "immediate": [],
        "short_term": [],
        "long_term": []
    }
    
    ripple_effects = calculate_ripple(
        action_power = significance,
        time_range = time_depth,
        affected_elements = get_affected_elements(action)
    )
```

## AI Behavior Guidelines
### Character Consistency
```yaml
Personality Maintenance:
  Check Points:
    - Core Values Alignment
    - Behavioral Consistency
    - Knowledge Boundaries
    - Relationship Memory
    - Development Track

Response Generation:
  Steps:
    1. Context Analysis
    2. Personality Filter
    3. Knowledge Check
    4. Emotional State
    5. Response Formation
    6. Consistency Verification
```

### World Logic Enforcement
```yaml
Physics Rules:
  - Magic System Compliance
  - Physical Limitations
  - Time Travel Rules
  - Divine Intervention Limits

Reality Checks:
  - Cause-Effect Validation
  - Power Scale Compliance
  - Timeline Consistency
  - Character Knowledge Limits
```

## Prompt Templates
### Character Interaction
```
Generate a response for [Character] in the following situation:
Context: {detailed_situation}
Emotional State: {current_emotions}
Goals: {immediate_objectives}
Constraints:
- Must maintain [trait1, trait2]
- Must consider [knowledge/limitation]
- Must address [plot_point]

Response should include:
1. Internal reaction
2. External response
3. Physical actions
4. Magical effects (if applicable)
```

### Combat Scene
```
Generate a combat sequence with the following parameters:
Participants: {list_of_characters}
Environment: {location_details}
Stakes: {importance_level}
Power Scale: {combat_tier}

Required Elements:
1. Tactical decisions
2. Power demonstrations
3. Environmental interaction
4. Emotional impact
5. Consequence setup

Special Considerations:
- Power balance maintenance
- Character development opportunities
- Plot advancement hooks
```

### World Building
```
Generate location description for [Place]:
Required Elements:
- Visual atmosphere
- Magical presence
- Historical significance
- Current state
- Hidden elements

Integration Points:
1. Plot hooks
2. Character connections
3. Mystery elements
4. Future potential

Balance Requirements:
- Wonder vs Danger
- Magic vs Mundane
- Known vs Unknown
```

## Quality Control
### Consistency Checkers
```yaml
Character Check:
  - Personality Consistency
  - Power Level Adherence
  - Knowledge Boundaries
  - Relationship Accuracy
  - Development Path

World Check:
  - Magic System Compliance
  - Physical Laws Adherence
  - Timeline Consistency
  - Causal Chain Validity
  - Power Balance
```

### Error Detection
```python
def validate_content(generated_text):
    checks = {
        "personality_drift": check_personality_consistency(),
        "power_scale": validate_power_levels(),
        "plot_holes": check_plot_consistency(),
        "world_rules": validate_world_mechanics(),
        "character_knowledge": check_knowledge_bounds()
    }
    
    return {
        "valid": all(checks.values()),
        "issues": [k for k, v in checks.items() if not v],
        "corrections": generate_corrections(checks)
    }
```

### Auto-Correction Guidelines
```yaml
Common Issues:
  Personality Drift:
    Detection: Compare against base template
    Correction: Realign with core traits
    Prevention: Regular personality checks

  Power Scaling:
    Detection: Mathematical validation
    Correction: Scale adjustment
    Prevention: Power calculators

  Timeline Inconsistency:
    Detection: Chronology check
    Correction: Event realignment
    Prevention: Timeline tracking
```

