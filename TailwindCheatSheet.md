## initialize CLI tailwindcss
commmand: npx @tailwindcss/cli -i ./src/input.css -o ./src/output.css --watch

# 🌀 Tailwind CSS Cheat Sheet (Compact)

## 📦 Layout
- `container` – Responsive fixed width container
- `box-border` / `box-content`
- `block` / `inline-block` / `inline`
- `flex` / `inline-flex`
- `grid` / `inline-grid`
- `hidden`

## 🎯 Flexbox & Grid
- `flex-row` / `flex-col`
- `items-start` / `items-center` / `items-end`
- `justify-start` / `justify-center` / `justify-between`
- `gap-{x}` – Spacing between items
- `grid-cols-{n}` – Grid columns (e.g., `grid-cols-3`)
- `col-span-{n}` – Grid column span

## 📐 Spacing
- `m{t|r|b|l|x|y}-{n}` – Margin
- `p{t|r|b|l|x|y}-{n}` – Padding
- `space-{x|y}-{n}` – Space between children

## 📏 Sizing
- `w-{n}` / `h-{n}` – Width/Height
- `min-w-{n}` / `max-w-{n}`
- `min-h-{n}` / `max-h-{n}`
- Common values: `0`, `px`, `full`, `screen`, `1/2`, `1/3`, etc.

## 🎨 Colors
- `text-{color}-{n}` – Text color
- `bg-{color}-{n}` – Background color
- `border-{color}-{n}` – Border color
- Example: `bg-blue-500`, `text-gray-700`

## 🖍️ Typography
- `text-{xs|sm|base|lg|xl|2xl|...}`
- `font-{thin|light|normal|medium|semibold|bold|black}`
- `tracking-{tighter|tight|normal|wide|wider|widest}`
- `leading-{none|tight|snug|normal|relaxed|loose}`
- `truncate`, `uppercase`, `lowercase`, `capitalize`

## 🧱 Borders & Radius
- `border` / `border-{t|r|b|l}`
- `border-{n}` – Border width
- `rounded` / `rounded-{t|r|b|l|full|xl|2xl}`

## 🔍 Effects
- `shadow` / `shadow-{sm|md|lg|xl|2xl|inner|none}`
- `opacity-{0-100}`
- `hover:{}` – Add on hover (e.g., `hover:bg-blue-600`)

## 🔄 Transitions & Animations
- `transition` / `transition-{property}`
- `duration-{75|100|150|200|300|500|700|1000}`
- `ease-{linear|in|out|in-out}`

## 📱 Responsive Prefixes
- `sm:` / `md:` / `lg:` / `xl:` / `2xl:`
- Example: `md:flex`, `lg:text-xl`

## 🌙 Dark Mode
- `dark:` – Example: `dark:bg-gray-900`

## 🧪 Misc
- `cursor-{pointer|not-allowed|wait}`
- `z-{n}` – Z-index
- `overflow-{auto|hidden|scroll|visible}`
- `select-{none|text|all}`
- `resize` / `resize-none`

---

📝 Tip: Combine classes like this:

```html
<div class="flex items-center justify-between p-4 bg-blue-500 text-white rounded shadow-md">
  Hello Tailwind!
</div>

## ✍️ TEXT Utilities

### 🎨 Color & Alignment
- `text-{color}-{n}` – e.g. `text-red-500`
- `text-left` / `text-center` / `text-right` / `text-justify`

### 🔠 Font Size
- `text-xs` – 0.75rem
- `text-sm` – 0.875rem
- `text-base` – 1rem
- `text-lg` – 1.125rem
- `text-xl` – 1.25rem
- `text-2xl` – 1.5rem
- `text-3xl` … up to `text-9xl`

### 🧵 Font Weight
- `font-thin` – 100
- `font-extralight` – 200
- `font-light` – 300
- `font-normal` – 400
- `font-medium` – 500
- `font-semibold` – 600
- `font-bold` – 700
- `font-extrabold` – 800
- `font-black` – 900

### ✏️ Font Style
- `italic` / `not-italic`

### 🔤 Text Transform
- `uppercase` / `lowercase` / `capitalize` / `normal-case`

### ✂️ Overflow & Truncation
- `truncate` – Single-line cut-off with ellipsis
- `overflow-ellipsis` – (Needs `overflow-hidden` & `whitespace-nowrap`)
- `break-words` / `break-all` / `whitespace-nowrap`

### 📏 Line Height (Leading)
- `leading-none`
- `leading-tight`
- `leading-snug`
- `leading-normal`
- `leading-relaxed`
- `leading-loose`

### 📏 Letter Spacing (Tracking)
- `tracking-tighter`
- `tracking-tight`
- `tracking-normal`
- `tracking-wide`
- `tracking-wider`
- `tracking-widest`

### 💬 Decoration & Shadow
- `underline` / `line-through` / `no-underline`
- `text-shadow` – (Needs custom plugin)
- `decoration-{color}` / `decoration-{style}`

---

🔥 Example:

```html
<p class="text-lg font-semibold text-center text-blue-700 uppercase tracking-wide leading-snug">
  Tailwind makes text styling easy!
</p>



# 🎨 Tailwind CSS COLOR Cheat Sheet

Each color comes in shades from `50` (lightest) to `900` (darkest).  
**Usage Example:** `bg-blue-500`, `text-red-700`, `border-green-300`

---

## 🧱 Gray Family

- `gray-50` → `gray-900`
- `slate-50` → `slate-900`
- `zinc-50` → `zinc-900`
- `neutral-50` → `neutral-900`
- `stone-50` → `stone-900`

---

## 🌈 Main Colors

- `red-50` → `red-900`
- `orange-50` → `orange-900`
- `amber-50` → `amber-900`
- `yellow-50` → `yellow-900`
- `lime-50` → `lime-900`
- `green-50` → `green-900`
- `emerald-50` → `emerald-900`
- `teal-50` → `teal-900`
- `cyan-50` → `cyan-900`
- `sky-50` → `sky-900`
- `blue-50` → `blue-900`
- `indigo-50` → `indigo-900`
- `violet-50` → `violet-900`
- `purple-50` → `purple-900`
- `fuchsia-50` → `fuchsia-900`
- `pink-50` → `pink-900`
- `rose-50` → `rose-900`

---

## 🎯 Special Colors

- `white`
- `black`
- `transparent`
- `current`
- `inherit`

---

## ✏️ Usage Examples

```html
<!-- Text Colors -->
<p class="text-red-500">Red Text</p>
<p class="text-gray-800">Gray Text</p>

<!-- Background Colors -->
<div class="bg-green-300 p-4">Success Box</div>

<!-- Borders -->
<div class="border border-blue-600 p-2">Bordered Box</div>

<!-- Hover States -->
<button class="hover:bg-indigo-500 text-white">Hover Me</button>

