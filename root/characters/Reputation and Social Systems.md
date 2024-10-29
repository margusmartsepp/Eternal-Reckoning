# Reputation Systems

## Individual Reputation
### Reputation Scores
```python
class ReputationSystem:
    def calculate_reputation(self, actor, faction):
        base_rep = self.get_base_reputation(actor, faction)
        action_modifier = sum(
            action.impact * action.relevance 
            for action in actor.recent_actions
        )
        
        relationship_modifier = self.calculate_relationship_impact(
            actor.relationships,
            faction.relationships
        )
        
        final_reputation = max(-1000, min(1000, 
            base_rep + action_modifier * relationship_modifier
        ))
```

### Fame/Infamy System
```yaml
Fame Levels:
  Unknown: 0-100
  Known: 101-300
  Notable: 301-600
  Famous: 601-900
  Legendary: 901+

Fame Effects:
  Quest Availability:
    Unknown: Basic only
    Known: +Uncommon
    Notable: +Rare
    Famous: +Epic
    Legendary: +Mythic

  Price Modification:
    Unknown: +20%
    Known: +10%
    Notable: +0%
    Famous: -10%
    Legendary: -20%
```

## Faction Relations
### Faction Standing
```python
class FactionStanding:
    def update_standing(self, action, actor):
        impact = action.base_impact * self.relevance_to_faction
        
        affected_relations = {
            faction: self.calculate_faction_impact(faction, impact)
            for faction in self.related_factions
        }
        
        ripple_effects = self.propagate_reputation_change(
            affected_relations,
            actor.influence_level
        )
```

### Political Power
```yaml
Power Metrics:
  Military Strength:
    Army Size: 30%
    Equipment Quality: 25%
    Training Level: 25%
    Magical Power: 20%

  Economic Power:
    Resource Control: 35%
    Trade Volume: 25%
    Currency Reserves: 20%
    Production Capacity: 20%

  Social Influence:
    Population Support: 40%
    Cultural Impact: 30%
    Diplomatic Relations: 30%
```

## Guild Systems
### Guild Ranks
```python
class GuildSystem:
    def calculate_rank_requirements(self, rank):
        return {
            'skill_level': RANK_BASE_SKILL[rank],
            'contribution_points': RANK_BASE_CONTRIBUTION[rank],
            'time_served': RANK_TIME_REQUIREMENT[rank],
            'achievements': RANK_ACHIEVEMENTS[rank],
            'special_requirements': RANK_SPECIAL[rank]
        }
    
    def evaluate_promotion(self, member):
        current_rank = member.rank
        next_rank = self.get_next_rank(current_rank)
        
        requirements = self.calculate_rank_requirements(next_rank)
        member_stats = self.get_member_stats(member)
        
        return all(
            member_stats[req] >= value 
            for req, value in requirements.items()
        )
```

### Guild Influence
```yaml
Influence Factors:
  Territory Control:
    Cities: 100 points each
    Resources: 50 points each
    Trade Routes: 75 points each

  Member Quality:
    Novice: 1 point
    Adept: 5 points
    Expert: 25 points
    Master: 100 points

  Economic Power:
    Market Share: 0-1000 points
    Asset Value: 0-1000 points
    Monthly Revenue: 0-1000 points
```

## Social Interaction
### Relationship Building
```python
class SocialInteraction:
    def calculate_interaction_result(self, actor, target, action):
        base_success = (
            actor.charisma 
            * action.effectiveness 
            * self.relationship_modifier
        )
        
        context_modifier = self.get_context_modifiers(
            location=self.current_location,
            time=self.current_time,
            witnesses=self.present_entities
        )
        
        result = {
            'success_chance': base_success * context_modifier,
            'reputation_impact': self.calculate_reputation_impact(),
            'relationship_change': self.calculate_relationship_change(),
            'social_consequences': self.determine_consequences()
        }
```

### Social Network
```yaml
Connection Types:
  Personal:
    Friend: +10 trust
    Family: +20 trust
    Mentor: +15 trust
    Student: +5 trust

  Professional:
    Guild: +5 trust
    Trade: +3 trust
    Political: +2 trust
    Military: +4 trust

Network Effects:
  Information Flow:
    Direct: 100% accuracy
    Secondary: 75% accuracy
    Tertiary: 50% accuracy

  Resource Access:
    Direct: 100% availability
    Secondary: 50% availability
    Tertiary: 25% availability
```