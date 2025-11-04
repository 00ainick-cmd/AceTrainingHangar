# Testing Instructions - AEA Training Terminal

## 🧪 How to Test the Fixed System

### Step 1: Clear Your Browser Cache
**IMPORTANT**: Your browser may be showing old cached files!

**Chrome/Edge:**
- Press `Ctrl+Shift+Delete` (Windows) or `Cmd+Shift+Delete` (Mac)
- Select "Cached images and files"
- Click "Clear data"
- OR do a hard refresh: `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac)

**Firefox:**
- Press `Ctrl+Shift+Delete` (Windows) or `Cmd+Shift+Delete` (Mac)
- Select "Cache"
- Click "Clear Now"

### Step 2: Open index.html
Open the file in your browser:
```
file:///home/user/AceTrainingHangar/index.html
```

### Step 3: What You Should See

#### **Main Dashboard:**
- Login screen asking for your name
- After login: Level, XP bar, Badges card, **NEW Analytics card**
- 4 module buttons: Classroom, Flashcards, Practice Test, Jeopardy

#### **Practice Test Module:**
✅ Should show:
- 6 colorful category cards
- Each card has icon, name, and question count
- 🧪 TEST SCORE button (purple, top-right)

❌ If you see:
- Blank white screen
- No categories
- Only the test button

**Then**: Clear cache and hard refresh!

#### **Flashcards Module:**
✅ Should show:
- Same 6 category cards as Practice Test
- 🧪 TEST SCORE button (purple, top-right)

#### **Jeopardy Module:**
✅ Should show:
- Full Jeopardy game board with categories
- Dollar values ($200-$1000)
- Player/AI score counters
- 🧪 TEST SCORE button (red, top-right)
- "End Session" button (when game starts)

### Step 4: Test XP System

1. **Click Practice Test**
2. **Click 🧪 TEST SCORE button**
3. **You should see:**
   - Alert showing: "XP Earned: +30" (not +15!)
   - Dashboard updates with new XP
   - Analytics card shows "Total Sessions: 1"
   - Analytics card shows "Lifetime XP: 30"

4. **Click Practice Test again**
5. **Click 🧪 TEST SCORE button again**
6. **You should see:**
   - Alert showing: "XP Earned: +5"
   - "XP Multiplier: 50%" message
   - Cumulative XP now 35

### Step 5: Test Score History

1. **After completing 2-3 modules**
2. **Click "View Score History" button** on analytics card
3. **You should see:**
   - List of all attempts with dates/times
   - XP earned per attempt
   - Improvement percentages

### Step 6: Test Debug Console

1. **Press F12** to open browser console
2. **Type:** `debugGameState()`
3. **Press Enter**
4. **You should see:**
   - Detailed breakdown of your progress
   - Module history with XP calculations
   - Current level and XP

---

## 🐛 Troubleshooting

### "I only see the test button, no categories"
- Clear browser cache completely
- Hard refresh (Ctrl+Shift+R)
- Close and reopen browser

### "XP is still not adding up"
- Check console for errors (F12)
- Run `debugGameState()` to see actual values
- Verify you're on the latest commit

### "Changes not appearing"
- You may be viewing old cached files
- Try opening in incognito/private window
- Check file modification dates

---

## ✅ Expected Results Summary

| Module | What Should Work |
|--------|-----------------|
| **Practice Test** | 6 categories visible, clickable, test button works |
| **Flashcards** | Same as Practice Test |
| **Jeopardy** | Full game board, playable, test button works |
| **XP System** | First attempt: 30 XP, Second: 5 XP (for 85%) |
| **Analytics** | Shows sessions, lifetime XP, modules, badges |
| **History** | Button shows all attempts with timestamps |

---

## 🧪 Test Button Behavior

The **🧪 TEST SCORE** buttons are FOR TESTING:
- They simulate completing a module
- Purple button (Practice/Flashcards): Simulates 85% score
- Red button (Jeopardy): Simulates 60% score (1200 player, 800 AI)
- These award XP to test the gamification system

**Note**: These are debugging tools. They can be removed for production if desired.
