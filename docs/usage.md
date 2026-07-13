<div dir="rtl" align="right">

# 📖 دليل الاستخدام — Promptium على كل منصة

هذا الدليل يشرح كيفية تفعيل Promptium على كل منصة، من اللصق المباشر إلى تحويله لمساعد دائم.

---

## 1️⃣ الاستخدام المباشر (أي نموذج)

الطريقة الأبسط وتعمل في كل مكان:

1. انسخ البرومبت الكامل من [`PROMPT.md`](../PROMPT.md).
2. الصقه كأول رسالة في المحادثة.
3. انتظر تأكيد النموذج، ثم اكتب فكرتك فقط — مثلاً: «فيديو تسويقي لمطعم».

> 💡 في المحادثات الطويلة قد «ينسى» النموذج التعليمات. إذا لاحظت ذلك، أعد لصق البرومبت أو ذكّره: «التزم بتنسيق الإخراج الإلزامي».

---

## 2️⃣ ChatGPT — تحويله إلى GPT مخصص (Custom GPT)

1. من القائمة اختر **Explore GPTs ← Create**.
2. في تبويب **Configure**:
   - **Name**: ‏Promptium — خبير هندسة الأوامر
   - **Description**: يحوّل أي فكرة إلى برومبت احترافي جاهز للاستخدام.
   - **Instructions**: الصق البرومبت الكامل من [`PROMPT.md`](../PROMPT.md).
3. في **Conversation starters** أضف أمثلة مثل: «برومبت لصورة شعار»، «برومبت لمقال تسويقي».
4. احفظ واختر مستوى المشاركة (خاص / برابط / عام).

---

## 3️⃣ Claude — عبر Projects أو claude.ai

**الطريقة الأولى — Claude Project (اشتراك Pro/Team):**
1. أنشئ **Project** جديداً باسم Promptium.
2. الصق البرومبت في حقل **Project Instructions**.
3. كل محادثة داخل المشروع ستعمل تلقائياً بشخصية خبير هندسة الأوامر.

**الطريقة الثانية — لصق مباشر:** الصق البرومبت كأول رسالة في أي محادثة.

> 💡 مع Claude تعطي [النسخة المتقدمة](../versions/prompt-advanced.ar.md) نتائج أفضل لأنها توجّه النموذج لاستخدام وسوم XML والتفكير خطوة بخطوة.

---

## 4️⃣ Gemini — تحويله إلى Gem

1. افتح **gemini.google.com** واختر **Explore Gems ← New Gem**.
2. **Name**: ‏Promptium.
3. **Instructions**: الصق البرومبت الكامل.
4. احفظ — سيظهر Gem جاهزاً في قائمتك الجانبية دائماً.

---

## 5️⃣ GitHub Copilot — مدمج تلقائياً في هذا المستودع ✨

هذا المستودع يحتوي على ملف [`.github/copilot-instructions.md`](../.github/copilot-instructions.md)، ما يعني أن **Copilot Chat يعمل بشخصية Promptium تلقائياً** داخل هذا المستودع دون أي إعداد:

1. افتح المستودع على github.com واضغط أيقونة **Copilot** (أو افتح المستودع في VS Code مع تفعيل Copilot Chat).
2. اكتب فكرتك مباشرة — مثلاً: «برومبت لصورة شعار مطعم» — وسيرد بالتنسيق الإلزامي الكامل.
3. لتفعيل الميزة نفسها في مستودعاتك الأخرى، انسخ الملف إلى `.github/copilot-instructions.md` فيها.

> 💡 في VS Code تأكد من تفعيل خيار `github.copilot.chat.codeGeneration.useInstructionFiles` في الإعدادات.

## 6️⃣ Grok

لا يوفر Grok حالياً مساعدين مخصصين دائمين، فاستخدم اللصق المباشر في بداية كل محادثة. مع السياق المحدود يُفضَّل استخدام [النسخة المختصرة](../versions/prompt-lite.ar.md).

---

## 7️⃣ مع مولّدات الصور والفيديو

Promptium **لا يُلصق داخل** Midjourney أو Stable Diffusion مباشرة — بل يعمل في نموذج محادثة (ChatGPT/Claude/Gemini) **لتوليد** البرومبت الذي تنسخه بعد ذلك إلى مولّد الصور أو الفيديو:

1. فعّل Promptium في نموذج المحادثة المفضل لديك.
2. اكتب فكرتك: «صورة إعلانية لعطر فاخر».
3. انسخ المخرجات الجاهزة (البرومبت + Negative Prompt + الإعدادات) إلى المولّد المستهدف.

---

## 8️⃣ عبر API (للمطورين)

مرّر البرومبت كـ `system` في طلبات API:

</div>

```python
# مثال مع Claude API
import anthropic

client = anthropic.Anthropic()

with open("PROMPT.md_extracted_text", encoding="utf-8") as f:
    PROMPTIUM = f.read()  # نص البرومبت من داخل كتلة الكود في PROMPT.md

response = client.messages.create(
    model="claude-sonnet-5",
    max_tokens=4096,
    system=PROMPTIUM,
    messages=[{"role": "user", "content": "برومبت لصورة قهوة عربية تراثية"}],
)
print(response.content[0].text)
```

<div dir="rtl" align="right">

> 💡 للاستخدام عبر API، تعطي [النسخة المختصرة](../versions/prompt-lite.ar.md) توازناً جيداً بين الجودة واستهلاك الرموز (Tokens).

---

## ❓ أسئلة شائعة

**أي نسخة أختار؟**

| الحالة | النسخة المناسبة |
|:---|:---|
| الاستخدام اليومي العام | [الأساسية](../PROMPT.md) |
| أعلى جودة ممكنة / منصات متعددة | [المتقدمة](../versions/prompt-advanced.ar.md) |
| سياق محدود / API / نماذج صغيرة | [المختصرة](../versions/prompt-lite.ar.md) |
| فرق أو نماذج إنجليزية | [الإنجليزية](../versions/prompt.en.md) |

**هل يعمل بلغات أخرى؟** نعم — أضف في نهاية البرومبت: «تفاعل معي بلغة [اللغة]».

</div>
