# Nexagen-Assignment
Assignment for an internship application (Nexagen)

# Reasons for using particular approaches

Using IMAP over POP3: 
Secure, Multiple device access, Faster, Syncs across devices

Using PostgreSQL over SQLite:
Better scalability, more flexibility

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
