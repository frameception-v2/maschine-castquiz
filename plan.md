### Step 1: Create Start Screen with Basic Navigation  
```text  
- Build: Frame with welcome image and "Begin Quiz" button that POSTs to /api/start  
- Outcome: Clicking button shows a new frame with hardcoded first question (verify via frame debugger)  
```  

### Step 2: Implement Quiz State Serialization  
```text  
- Build: State encoding/decoding system using base64 JSON with {c:current_question, s:score, q:question_hashes}  
- Outcome: After answering mock question, state appears in frame POST payloads (verify via request logs)  
```  

### Step 3: Farcaster Casts Integration  
```text  
- Build: /api/start endpoint that fetches user's casts via Farcaster API using fid from frame message  
- Outcome: Logs show 2 real cast texts being selected (test with known active fid)  
```  

### Step 4: Basic Answer Validation Flow  
```text  
- Build: /api/answer endpoint that compares responses to stored answers and updates state  
- Outcome: Correct answers increment score (verify via final score display)  
```  

### Step 5: Distractor Answer Generation  
```text  
- Build: Integration with 3rd party distractor service for fake options (mock first, then real API)  
- Outcome: Question screens show 4 options with 1 correct + 3 plausible alternatives  
```  

### Step 6: Progress-Driven Frame Rendering  
```text  
- Build: Dynamic image endpoints showing question numbers and final score  
- Outcome: Visual verification of different images at each stage via frame simulator  
```  

### Step 7: State Validation & Error Recovery  
```text  
- Build: State checksum validation and fallback to Farcaster trivia when cast fetch fails  
- Outcome: Tampered state shows error message, empty cast history uses backup questions  
```  

### Step 8: Performance Optimization  
```text  
- Build: Caching layer for frequent user profiles and pre-generated distractor answers  
- Outcome: API response times under 500ms measured in monitoring  
```