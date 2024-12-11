## **Transforming Chaos: An NLP Approach to Multiverse Narrative**

12/10/2024  
Chelsea Chen  
Project Type: Implementation 

#### 

### **Problem Definition**

The movie *Everything Everywhere All at Once* presents a unique challenge for script analysis due to its non-linear, multiverse narrative. Its script reflects themes of chaos, interconnectedness, and fragmentation, making it an ideal test case for exploring how computational methods can extract meaning from unconventional texts.

For this project, I focused on the key questions: How can computational techniques help us organize and interpret complex texts that are challenging even for human readers? How can meanings be derived from chaotic data? 

By applying Natural Language Processing (NLP) techniques, I aimed to transform the movie script into a structured dataset and analyze how thematic focuses vary across different parts and universes.

#### 

### **Approach**

**1\. Text Preprocessing** Preprocessing the script was an essential step to prepare the data for analysis. I followed techniques covered in class, including:

* **Tokenization**: I used SpaCy to break the script into individual words (tokens). This step was important for downstream analysis like frequency counting and TF-IDF.  
* **Lemmatization**: Each token was reduced to its base form, allowing words like "running" and "ran" to be treated as the same term.  
* **Stopword Removal**: Common words like "the" and "and" were removed to focus on more meaningful terms.

Additionally, I performed specific processing for the script:

* **Removing Redundant Content**: Since the script includes both English and Chinese dialogues (with English translations alongside), I removed lines containing Chinese characters to facilitate analysis. However, mixed English and Chinese dialogues could not be fully resolved, leaving some redundancy.  
* **Cleaning Page Numbers and Headers**: Elements like page numbers (e.g., "1.") and scene headers  (e.g., "INT. LAUNDROMAT \- THAT MOMENT") were removed or repurposed as metadata.

These steps aligned with the text preprocessing concepts discussed in class, such as tokenization and lemmatization, and allowed me to prepare the data for structured analysis.

**2\. Metadata** One of the advantages of working with movie scripts is the structured format, which includes metadata like scene numbers, universe names, and part titles. I used this information to annotate the text and organize it into manageable units:

* **Scenes and Sub-Scenes**: Using regular expressions, I extracted scene numbers (e.g., "16") and sub-scene numbers (e.g., "107-1" or "A107"). Each scene or sub-scene was stored as a separate row.  
* **Universes**: Scene headers often included universe names, such as "ALPHAVERSE" or "MOVIE STAR UNIVERSE." I wrote a function to extract these names and maintained the current universe until a new one appeared. For the first 18 scenes, which lacked universe labels, I manually assigned "ORIGINAL UNIVERSE" based on contexts.  
* **Parts**: The script is divided into three parts: "PART 1: EVERYTHING," "PART 2: EVERYWHERE," and "PART 3: ALL AT ONCE." I extracted these labels from the script and assigned them to the relevant sections.

These metadata annotations helped organize the chaotic script into structured units, reflecting principles of information retrieval and hierarchical organization discussed in class.

**3\. Term Analysis** With the text preprocessed and annotated, I analyzed term frequencies to explore how language reflected the movie’s themes:

* **Word Frequency**: I identified the 30 most frequent words in the script. Unsurprisingly, character names like "evelyn" and "waymond" dominated, but thematic terms like "universe," "bagel," and "rock" also appeared prominently.  
* **TF-IDF**: To move beyond raw counts, I applied Term Frequency-Inverse Document Frequency (TF-IDF), a key concept discussed in class. I first conducted an analysis across three parts to capture key themes and narrative shifts. Similarly, I performed analyses across universes to explore unique linguistic patterns in each setting. Among the 18 universes, the top 6 by content length were analyzed.   
  As mentioned in class, multiword expressions often provide more valuable information. Thus, to refine the analysis, I performed a bigram TF-IDF and excluded character names to focus on thematic patterns and contextual language. These analyses provided insights into the movie’s narrative structure and how language shifts across its parts and universes.  
* **Visualization** I presented findings through word clouds, bar charts, and heatmaps, allowing for easy comparison of term distributions across parts and universes.

### **Findings**

**1\. Part Analysis**

The TF-IDF analysis by part reveals how language reflects the movie’s shifting themes. In Part 1 (Everythiing), the focus is on family dynamics, with terms like "joy," "becky," and "mom" highlighting Evelyn’s grounded struggles. Part 2 (Everywhere) shifts to multiverse chaos, introducing terms like "alpha," "universe," and "jobu" that emphasize action and philosophical conflict. Finally, Part 3 (All at Once) resolves these tensions, with terms like "bagel" and "rock" symbolizing Evelyn’s acceptance of her fragmented existence and reconnection with her family.

**2\. Universe Analysis** 

The TF-IDF analysis across universes reveals the shifting prominence of key characters and the unique focus of each setting. The Original Universe highlights mundane setting and familial conflicts, with terms like "elevator door" and "divorce paper", while Evelyn, Waymond, and Joy dominate as central figures. The Alphaverse and Action Universe focus on high-stakes multiverse exploration, with terms like "verse jump" and “grab” showing the actions and chaos. Gong Gong and Jobu emerge more prominently. The Taxes Universe blends mundane and emotional struggles, featuring Waymond’s "googly eye" philosophy and the recurring tension with Deirdre. In the Movie Star Universe, terms like "movie star," "kung fu," and “ceo” reflect Evelyn and Waymond’s alternate life of glamor and success, in contrast to the Original and Taxes Universes. The Temple Universe mainly focuses on the interaction between Evelyne and Jobu, where terms like "bagel" and "daughter" reflect Evelyn’s reconciliation with Joy/Jobu. Across all universes, Evelyn’s dominance underscores her central role, while the shifting importance of Waymond, Gong Gong, Joy/Jobu highlights the evolving dynamics in between Evelyn and her family throughout the multiverse narrative.

### **Reflection**

This project demonstrated the value of computational techniques for structuring and analyzing unconventional scripts. Class concepts like tokenization, lemmatization, regular expressions, and TF-IDF were instrumental in extracting meaningful patterns from chaotic data. 

A significant aspect of this project was converting the movie script into a structured dataset. This transformation process highlights how raw data can be turned into a format that enables deeper exploration and analysis. It represents the essence of information organization and retrieval: creating an organized, searchable framework for chaotic data that makes it possible to extract meaningful insights. 

**Challenges and Limitations:** Given the nature of this script, it has been challenging to preprocess the texts, and some tasks could not be achieved within the limited timframe. Separating dialogue from descriptions would have provided richer insights but turned out to be infeasible due to the lack of explicit markers. This would require advanced techniques like machine learning models. The scene header also contains valuable information like location that could add to the analysis. But due to the irregular header patterns, I wasn’t able to parse location data. Additionally, the script’s fragmented, multiverse-driven structure and intertwined storylines made it difficult to fully exact themes across universes, and manual intervention may be required for tasks like assigning universes to unlabeled scenes to get more accurate metadata.

**Future Directions**: Given more time, I would implement more advanced methods, such as machine learning or large language models to classify dialogues and descriptions and annotate other metadata like universes. I would also perform sentiment analysis to track emotional changes across parts, universes, and scenes. I could also explore character interactions by analyzing word co-occurrences and conversational patterns.

Overall, this analysis offered a unique perspective on how language reflects the themes of *Everything Everywhere All at Once*, showing how computational methods can uncover insights even in chaotic, fragmented narratives.

