# Opponent-Behavior-Prediction-Engine
# OpponentTracker.py

class OpponentTracker:
    def __init__(self, opponent_id: str):
        self.opponent_id = opponent_id
        # Tracks the count of each action taken by the opponent
        self.action_history_counts: dict[str, int] = {} 

    def record_action(self, action_name: str):
        """Records an action taken by the opponent."""
        self.action_history_counts[action_name] = self.action_history_counts.get(action_name, 0) + 1

    def predict_most_frequent_action(self) -> str:
        """Predicts the opponent's next action based on overall historical frequency."""
        if not self.action_history_counts:
            return "Neutral_Stance" # Default if no data
        
        # Find the action with the maximum count
        most_frequent = max(self.action_history_counts, key=self.action_history_counts.get)
        return most_frequent

# Example Usage
if __name__ == "__main__":
    tracker = OpponentTracker("Rival_Agent_X")
    
    # Simulate recorded actions over time
    tracker.record_action("Defend_Point_A")
    tracker.record_action("Rush_Center")
    tracker.record_action("Defend_Point_A")
    tracker.record_action("Flank_Left")
    tracker.record_action("Defend_Point_A")
    
    print(f"Predicted Next Action for {tracker.opponent_id}: {tracker.predict_most_frequent_action()}")
