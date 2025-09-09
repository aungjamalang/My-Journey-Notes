
## **Git အခြေခံ (Basic Commands)**

|အမည်|Git Command|မြန်မာ အဓိပ္ပာယ်|
|---|---|---|
|Repository စတင်ရန်|`git init`|လက်ရှိ ဖိုလ်ဒါကို Git repository အဖြစ် စတင်ရန်|
|Repository ကနေ clone လုပ်ရန်|`git clone <repo_url>`|အခြား Git repository ကို မိမိ local machine သို့ ဒေါင်းလုပ်လုပ်ရန်|
|Status စစ်ရန်|`git status`|လက်ရှိ repository မှာ ဘာများပြောင်းလဲထားပြီး ဘာများ staged ဖြစ်ထားသည် စစ်ရန်|
|ဖိုင်များ add လုပ်ရန်|`git add <file>`|ဖိုင်များကို commit အတွက် stage လုပ်ရန်|
|အားလုံး add လုပ်ရန်|`git add .`|လက်ရှိ directory အတွင်းရှိ ဖိုင်အားလုံးကို stage လုပ်ရန်|
|Commit လုပ်ရန်|`git commit -m "message"`|Stage လုပ်ထားသော ဖိုင်များကို commit လုပ်ပြီး message ထည့်ရန်|
|Commit history ကြည့်ရန်|`git log`|Repository ရဲ့ commit history ကြည့်ရန်|

---

## **Branch (ခွဲခေါင်း) စီမံခြင်း**

|အမည်|Git Command|မြန်မာ အဓိပ္ပာယ်|
|---|---|---|
|လက်ရှိ branch ကြည့်ရန်|`git branch`|Repository မှာ ဘယ် branch မှာ ရှိနေသည် စစ်ရန်|
|Branch အသစ် ဖန်တီးရန်|`git branch <branch_name>`|အသစ် branch ဖန်တီးရန်|
|Branch ပြောင်းရန်|`git checkout <branch_name>`|အခြား branch သို့ ပြောင်းရန်|
|Branch အသစ် ဖန်တီးပြီး ပြောင်းရန်|`git checkout -b <branch_name>`|အသစ် branch ဖန်တီးပြီး တိုက်ရိုက် ပြောင်းရန်|
|Branch ဖျက်ရန်|`git branch -d <branch_name>`|မလိုအပ်သော branch ဖျက်ရန်|
|Force ဖြင့် branch ဖျက်ရန်|`git branch -D <branch_name>`|Merge မပြီးပဲ branch ဖျက်ရန်|

---

## **Remote (အဝေး) Repository စီမံခြင်း**

| အမည်                       | Git Command                              | မြန်မာ အဓိပ္ပာယ်                                  |
| -------------------------- | ---------------------------------------- | ------------------------------------------------- |
| Remote repository ကြည့်ရန် | `git remote -v`                          | အဝေး repository URL ကြည့်ရန်                      |
| Push လုပ်ရန်               | `git push origin <branch_name>`          | Local commit ကို remote သို့ ပို့ရန်              |
| Pull လုပ်ရန်               | `git pull`                               | Remote repository မှ အချက်အလက်များ update လုပ်ရန် |
| Remote branch ဖျက်ရန်      | `git push origin --delete <branch_name>` | Remote branch ဖျက်ရန်                             |

---

## **အခြား အရေးကြီး Command များ**

|အမည်|Git Command|မြန်မာ အဓိပ္ပာယ်|
|---|---|---|
|Diff ကြည့်ရန်|`git diff`|မပြောင်းလဲသေးသော ဖိုင်များ ကြည့်ရန်|
|Commit undo (most recent)|`git commit --amend`|နောက်ဆုံး commit ကို ပြန် edit လုပ်ရန်|
|Reset to previous commit|`git reset --hard <commit_hash>`|အရင် commit အတိုင်း repository ပြန်သတ်မှတ်ရန်|
|Stash changes|`git stash`|လက်ရှိပြောင်းလဲမှုများကို အချိန်အနည်းငယ် ဖျောက်ရန်|
|Stash ပြန်ယူရန်|`git stash pop`|ဖျောက်ထားသော changes ပြန်ယူရန်|

---

💡 **Tip:**

- `git add` → stage
    
- `git commit` → save
    
- `git push` → remote သို့ ပို့