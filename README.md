# Gaming-Track-
# The solution of Addressing Consumer Issues like Online Harassment, Data Privacy, Fraud Prevention, Addiction Management, transparency and Differentiating Gaming vs. Gambling


    import re
    import time
    from cryptography.fernet import Fernet
    from sklearn.ensemble import IsolationForest
    import numpy as np
    from hashlib import sha256

# 1. Online Harassment Detection
    class HarassmentDetector:
      def __init__(self):
        self.abusive_patterns = [r'badword1', r'badword2']  # Add more patterns as needed

      def detect_abusive_language(self, message):
        for pattern in self.abusive_patterns:
            if re.search(pattern, message, re.IGNORECASE):
                return True
        return False

# 2. Data Privacy Management
    class DataPrivacy:
      def __init__(self):
        self.key = Fernet.generate_key()
        self.cipher_suite = Fernet(self.key)

      def encrypt_data(self, data):
        return self.cipher_suite.encrypt(data.encode())

      def decrypt_data(self, encrypted_data):
        return self.cipher_suite.decrypt(encrypted_data).decode()

# 3. Fraud Prevention using Anomaly Detection


    class FraudDetector:
      def __init__(self, data):
        self.model = IsolationForest()
        self.model.fit(data)

      def detect_fraud(self, new_data):
        return self.model.predict(new_data)

# 4. Addiction Management

    class GameSession:
      def __init__(self):
        self.start_time = time.time()

      def check_playtime(self):
        elapsed_time = time.time() - self.start_time
        if elapsed_time > 3600:  # 1 hour
            return "You've been playing for over an hour. Consider taking a break!"
        return "Keep enjoying your game!"

# 5. Transparency in Gameplay Mechanics

    class GameTransaction:
      def __init__(self, player_id, action):
        self.player_id = player_id
        self.action = action
        self.hash = self.generate_hash()

      def generate_hash(self):
        return sha256(f"{self.player_id}{self.action}".encode()).hexdigest()

# 6. Differentiating Gaming vs. Gambling

    class Game:
      def __init__(self, name, skill_based, chance_based):
        self.name = name
        self.skill_based = skill_based
        self.chance_based = chance_based

      def classify_game(self):
        if self.skill_based and not self.chance_based:
            return "Skill-based Game"
        elif not self.skill_based and self.chance_based:
            return "Gambling"
        else:
            return "Mixed"

# Example Usage


    if __name__ == "__main__":
      # Online Harassment Detection
      harassment_detector = HarassmentDetector()
      message = "You are such a badword1!"
      if harassment_detector.detect_abusive_language(message):
        print("Abusive language detected!")
      else:
        print("No abusive language detected.")

    # Data Privacy Management
    data_privacy = DataPrivacy()
    encrypted = data_privacy.encrypt_data("User  sensitive data")
    print("Encrypted data:", encrypted)
    print("Decrypted data:", data_privacy.decrypt_data(encrypted))

    # Fraud Prevention
    sample_data = np.array([[1, 2], [1, 1], [2, 2], [10, 10]])  # Normal and anomalous data points
    fraud_detector = FraudDetector(sample_data)
    new_data = np.array([[1, 2], [10, 10]])  # New user behavior
    print("Fraud predictions:", fraud_detector.detect_fraud(new_data))

    # Addiction Management
    session = GameSession()
    time.sleep(3700)  # Simulate playtime
    print(session.check_playtime())

    # Transparency in Gameplay Mechanics
    transaction = GameTransaction("player123", "win")
    print("Transaction hash:", transaction.hash)

    # Differentiating Gaming vs. Gambling
    game1 = Game("Chess", True, False)
    game2 = Game("Slot Machine", False, True)
    print(game1.classify_game())  # Skill-based Game
    print(game2.classify_game())  # Gambling
