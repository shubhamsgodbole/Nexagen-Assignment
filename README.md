# Nexagen-Assignment
Assignment for an internship application (Nexagen)

# Reasons for using particular approaches

Using IMAP over POP3: 
Secure, Multiple device access, Faster, Syncs across devices

Using PostgreSQL over SQLite:
Better scalability, more flexibility

# Video Links
Link to detailed explanation of code (watch on 1.2x speed): https://www.loom.com/share/5b217bb1d9f54450bbc68051a78426d2?sid=7286ce3c-2c8c-47fd-ac37-19918d57d2be

Link to quick demo (watch on 1.2x speed): https://www.loom.com/share/443e02e4a0ff4011a6e7fa6bddfdd5e0?sid=d3f84ed9-32a8-4286-95cc-7bdd1c22cc3b

# EmailClassifier code segment explanation
The EmailClassifier class has been created to classify emails into predefined categories: promotions, work, finance, personal, etc., based on subject and body content.

Core Model:
Uses the SentenceTransformer model (paraphrase-MiniLM-L3-v2) for embedding and semantic analysis.

Category Setup:
Each category has primary (important keywords) and context (supporting phrases) with specific weights.

Enhanced Embeddings:
Precomputes weighted embeddings for each category's primary and context phrases for efficient comparison.

Sliding Context Windows:
Splits the email content into overlapping windows (5 words on each side) for better context extraction.

Similarity Analysis:
Uses cosine similarity to calculate the relevance of email text to each category’s primary and context embeddings.

Scoring:
Combines similarity scores with weights (0.7 for primary and 0.3 for context) to compute overall category scores.

Classification Logic:
Identifies the top 2 categories by score and evaluates:
Confidence, Score difference, Thresholds for ambiguity or dominance

Fallback Mechanism:
Returns "unknown" category for empty or error cases.

Preprocessing:
Cleans text by removing HTML tags, special characters, and normalizing spaces.
