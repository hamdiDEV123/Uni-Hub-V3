# Uni Hub Connect

> **Uni-Hub-v1** | The Ultimate University Hub for students to manage studies, life, and daily habits with smart workflow and pomodoro.

## 🚀 نظرة عامة

مشروع React/TypeScript مصمم لطلاب الجامعة، يجمع بين:
- لوحة متابعة 5 أقسام ذكية (ديني، دراسي، مهني، صحي، شخصي).
- نظام تحديات يومية ديناميكي.
- واجهة بومودورو متكاملة ومتعطشة للتركيز.
- تتبع تقدم تكليفات، مراجعة محاضرات، جلسات تركيز مهيكلة.

> مشروع مبني على Vite، برمجته ملفوفة بواحد من أحدث تجارب Dev في React 18.

---

## 🧩 بنية المشروع

- `src/` - الكود المصدر الرئيسي
  - `pages/` - صفحات الرتبط مثل `Workspace`, `Study Hub`, `Dashboard`...
  - `components/` - مكونات UI عامة ومجموعات workspace
  - `components/workspace` - مجموعة أقسام الحياة و`StudyWorkspace` وبومودورو
  - `lib/` - business logic، schema، migrations
  - `hooks/` - state hooks (مثل `useWorkspaceData`)
- `scripts/` - سكريبتات معينة مثل تقرير `as-never` و (يمكن إضافة `claude-test`)
- `supabase/` - ترحيلات قاعدة بيانات
- `public/` - static files

---

## 🧪 تقنيات أساسية

- `React 18` + `React Router 6`
- `TypeScript` الشامل
- `Vite` كـ build tool بساطة سرعة
- `TailwindCSS` + `Radix UI` + `Sonner` للأناقة
- `@tanstack/react-query` للـ state و cache
- `Supabase` integration (باك إند)
- `Sentry` error tracking

---

## 🛠️ تشغيل المشروع

1. تثبيت الحزم

```bash
npm install
```

2. تشغيل السيرفر

```bash
npm run dev
```

3. بناء لإنتاج

```bash
npm run build
```

4. اختبار

```bash
npm run test
```

5. معاينة الإنتاج

```bash
npm run preview
```

---

## 🧭 architecture حديثة

- `useWorkspaceData`: إدارة الداتا المحلية، reset يومي، progress حسابي لكل قسم
- `sectionProgress` في `src/lib/workspace/schema.ts`: يوزن 3 مؤشرات (دراسة) أو 8 عناصر (ديني)
- `Workspace` page: صفحة رئيسية + صفحان فرعيان `SectionDetails` ثم `StudySection` + بقية الأقسام.

---

## 📚 Workflow القسم الدراسي (Study)

- `StudySection` يعرض بطاقة:
  - تقدم (percentage)
  - المهام المكتملة (`focusSessions / focusTarget`)
  - تقدم التكليف (`assignmentProgress`)
  - مراجعة المحاضرات (`lecturesReviewed`)
- حركة Pomodoro متكاملة عبر `StudyWorkspace`:
  - tasks list
  - start session (tasks + custom minutes)
  - warmup
  - `ZenFocusTimer`
  - sound و complete callback

---

## 🌐 إدارة بومودورو منفصل

- مكون `src/pages/Pomodoro.tsx` يقوم:
  - عرض تفاصيل مهمة/وقت
  - موفِّر واجهة full-screen
  - `StudyWorkspace` داخلها في view `pomodoro`
  - route: `/workspace/pomodoro?section=study&taskTitle=...&minutes=...`

---

## 💡 التحسينات والتطوير القادمين

- فصل task state عن تركيز جلسات `focusSessions` لتصبح مهمة قائمة بذاتها
- analytics بعمق: سجل جلسات، فترات استراحة، أداء أسبوعي، تقارير
- مكافآت وإنجازات: `streaks`, `badge` لكل هدف
- دعم أداة صوت/تحديث بـ API (Claude/ChatGPT) لكتابة ملخصات المهام

---

## 🧹 قواعد تنسيق الكود و git

- استخدم ESLint + Prettier
- الفرع `main` لمستقر
- feature branches باسم `feature/*`
- commit message طريقة:
  - `feat:`, `fix:`, `chore:`, `refactor:`

---

## 🔐 config & secrets

ملف `.env` (مثال):

```dotenv
VITE_SUPABASE_URL=...
VITE_SUPABASE_ANON_KEY=...
VITE_SENTRY_DSN=...
ANTHROPIC_API_KEY=...
```

- لا ترفع `.env` للريبو.
- أضف `.env.local` للبيئة المحلية عند الحاجة.

---

## 🪓 أوامر إضافية

- `npm run lint`
- `npm run typecheck`
- `npm run as-never:report`

---

## 🔧 مشاركة وتعاون

1. fork / clone المشروع
2. branch بعنوان feature/task
3. PR مع وصف + أوامر للتجربة
4. نظرة كود، reviewers، merge بعد توافق

---

## 📌 سطر النهاية

> **Uni-Hub-v1** هو مشروع مبني لتجربة مستخدم واقعي للطالب مع تركيز عالي وهندسة صحيحة للـ state. هدفنا الآن: يبقى أغلى مشروع محفظتك ذات واجهة مسقوفة، أداء عالي، واجهة لطيفة، وتجربة Pomodoro لا تُنسى.
