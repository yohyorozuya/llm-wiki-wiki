# Mehul Gupta — LLM Wiki critique & explainer series (Data Science in Your Pocket, Medium)

Sources: several April 2026 Medium posts by Mehul Gupta. Fetched late May 2026.

## "Andrej Karpathy's LLM Wiki is a Bad Idea" (Apr 11, 2026)

Core argument (verbatim themes):
- "This is not a 'bye bye RAG' moment. In fact, LLM-Wiki can very easily turn into a messy and unreliable system."
- The crucial contrast: with RAG, "the model goes back to the original documents each time. Even if it makes a mistake once, the next query has a chance to correct it because the source is still the same. LLM-Wiki changes that completely." In a wiki, an error written into a page persists and is reused.
- The pitch "sounds like how humans learn" and feels "smarter, faster, more organized" — but the cracks show on reflection.

## "LLM Wiki: Bye Bye RAG" (Apr 7, 2026)

- Acknowledges the idea is powerful but notes the DIY assembly problem: "stitching it together yourself (Obsidian vaults, Web Clipper, Claude prompts, custom scripts, weekly linting) is exactly the 'hacky collection of scripts' [Karpathy] wanted to move beyond."

## "LLM Knowledge Bases explained" (Apr 20, 2026)

- The Golden Rule: "Karpathy rarely touches the Wiki files himself. He treats the Wiki as 'AI territory.' The AI writes it, updates it, and maintains it. Karpathy just reads it."
- The compiler analogy: "the AI takes the messy raw files and 'compiles' them into a Wiki." AI does summarizing, categorizing, linking (backlinks), writing articles.
- Workflow: Collect → Compile → View (Obsidian) → Ask → Create (slides/charts/notes added back) → Maintain.
- Karpathy "points out that right now, this is a 'hacky' collection of scripts. But he believes there is a huge opportunity here for someone to build a polished product."

## "LLM-Wiki vs RAG" (Apr 11, 2026)

- "RAG treats knowledge like a large folder of files... The system does not change the files or build anything new, it just looks again and again. LLM Wiki, on the other hand, tries to actively organize knowledge."

## "Graphify" (Apr 9, 2026)

- Frames both LLM Wiki and graph approaches as solving the same deeper issue: "AI systems are stateless." "Andrej Karpathy showed that organizing knowledge once is better than querying it repeatedly. Graphify pushes that idea further by turning everything into a connected system you can navigate."
