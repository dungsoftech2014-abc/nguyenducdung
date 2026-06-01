# Authentication Pages Documentation

## Project Overview

This document outlines the design specifications and implementation details for the authentication system, including login and registration pages. It serves as a comprehensive guide for maintaining consistency across all future basic pages.

---

## Pages Created

### 1. login.html
**Purpose:** Enable users to securely access their existing accounts

**Key Features:**
- Email and password input fields
- Remember me checkbox functionality
- Forgot password link
- Social login buttons (Google, GitHub, Facebook)
- Visual feedback and hover effects
- Navigation link to registration page

**Key Components:**
- Email field with mail icon
- Password field with lock icon
- Sign in button (primary CTA)
- Social authentication options
- Responsive grid layout (left: info + features, right: form)

---

### 2. register.html
**Purpose:** Allow new users to create accounts with comprehensive information collection

**Key Features:**
- Full name input (required)
- Email input (required)
- Phone number input (optional, 10 digits validation)
- Gender dropdown (optional)
- Address input (optional)
- Password input (required)
- Confirm password with validation
- Terms & conditions checkbox (required)
- Password mismatch error handling
- Navigation link to login page

**Key Components:**
- User icon for full name
- Mail icon for email
- Phone icon for phone number
- Map pin icon for address
- Lock and check-circle icons for passwords
- Scrollable form area for long content
- Real-time password confirmation validation
- Terms agreement link

---

## Design System

### Color Palette
```
Dark Background:    #090A14  (Primary background, very dark navy)
Surface Layer:      #10121E  (Slightly lighter for containers)
Inner Surface:      #0B0C17  (Form background, darker variant)
Card Background:    #0F111E  (Feature cards and accents)
Input Background:   #11141E  (Form input fields)
Border Color:       #272A3C  (Subtle borders for separation)
Primary/CTA:        #DF6B33  (Orange - buttons and highlights)
Dark CTA Hover:     #c95c2c  (Darker orange on hover)
Muted Text:         #8D93A1  (Secondary text, disabled state)
Text Primary:       #FFFFFF  (Main text color)
Error Color:        #EF4444  (Validation errors - red-400)
```

### Typography
```
Headings:
- Font Family:    Poppins (Google Fonts)
- Font Weight:    700 (bold) to 800 (extra bold)
- Font Size:      2.5rem (h1) to 1.875rem (h2)

Body Text:
- Font Family:    Inter (Google Fonts)
- Font Weight:    400 (regular), 500 (medium)
- Font Size:      0.875rem (labels) to 1rem (body)

Font Links:
https://fonts.googleapis.com/css2?family=Inter:wght@400;500&family=Poppins:wght@700;800&display=swap
```

### Icons Library
- **Source:** Lucide Icons (v0.450.0+)
- **CDN:** https://cdn.jsdelivr.net/npm/lucide@^0.450.0/dist/lucide.min.js
- **Usage:** `<i data-lucide="icon-name" class="h-5 w-5"></i>` then call `lucide.replace()`

**Icons Used:**
- `mail` - Email fields
- `lock` - Password fields
- `check-circle` - Password confirmation
- `user` - Full name field
- `phone` - Phone number field
- `map-pin` - Address field
- `google` - Google login button
- `github` - GitHub login button
- `facebook` - Facebook login button

---

## Layout & Responsive Design

### Breakpoints
- **Mobile First Approach:** Default styles for mobile (px-4)
- **Tablet (sm:):** 640px and above (sm:px-6)
- **Desktop (lg:):** 1024px and above (lg:px-8)

### Container Structure
```
Main Container
├── Outer Container (max-w-4xl, rounded-[32px])
│   └── Grid Layout (2 columns on desktop, 1 on mobile)
│       ├── Left Column (1.1fr width)
│       │   ├── Welcome Section (title, description)
│       │   └── Feature Cards (3-column grid)
│       └── Right Column (0.9fr width)
│           └── Form Container
│               ├── Header with Icon
│               ├── Form Fields
│               └── Navigation Link
```

### Responsive Breakpoints
- **Mobile:** Full width, vertical layout, single column
- **Tablet (sm:):** Adjusted padding, stacked elements
- **Desktop (lg:):** 2-column grid layout with left info panel

---

## Form Components

### Input Field Structure
```html
<label class="block text-sm font-medium text-muted">
  Field Label
  <div class="mt-2 flex items-center gap-3 rounded-3xl border border-border 
              bg-[#11141E] px-4 py-3 transition focus-within:border-focus">
    <i data-lucide="icon-name" class="h-5 w-5 text-muted"></i>
    <input type="type" placeholder="..." class="..." required />
  </div>
</label>
```

### Checkbox Structure
```html
<label class="inline-flex items-center gap-3 text-sm text-muted">
  <input type="checkbox" class="h-4 w-4 rounded border-border bg-[#11141E] 
                              text-focus focus:ring-focus" />
  Label Text
</label>
```

### Select Dropdown Structure
```html
<select class="w-full rounded-3xl border border-border bg-[#11141E] px-4 py-3 
               text-white outline-none transition focus:border-focus">
  <option>...</option>
</select>
```

### Button Structure
```html
<button type="submit" class="w-full rounded-3xl bg-[#DF6B33] px-5 py-4 
                             text-base font-semibold text-white 
                             transition hover:bg-[#c95c2c]">
  Button Text
</button>
```

---

## Validation Rules

### Email
- Type: `type="email"`
- Required: Yes
- Pattern: Standard email format

### Password
- Type: `type="password"`
- Required: Yes
- Confirmation: Must match in register form
- Error Message: "Passwords do not match"

### Phone Number
- Type: `type="tel"`
- Required: No (optional)
- Max Length: 10 characters
- Pattern: `[0-9]{10}` (numbers only)

### Full Name
- Type: `type="text"`
- Required: Yes (register only)
- Pattern: Any text

### Terms & Conditions
- Type: `type="checkbox"`
- Required: Yes (register only)
- Must be checked before submission

### Gender
- Type: `<select>`
- Required: No (optional)
- Options: Male, Female, Other, Prefer not to say

### Address
- Type: `type="text"`
- Required: No (optional)
- Pattern: Any text

---

## Shadow & Effects

### Container Shadow
```css
box-shadow: 0 24px 80px rgba(0, 0, 0, 0.45);
backdrop-filter: blur(12px);
```

### Card Shadow
```css
box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
```

### Transitions
- Default: All color changes with smooth transition
- Duration: 200ms (Tailwind default)
- Properties: `transition` on hover elements

---

## Design Rules for Future Pages

### 1. Color & Theme Consistency
- **Always use the defined color palette** - no arbitrary color values
- Dark theme only (#090A14 as primary background)
- Primary action color is always #DF6B33
- Maintain the same dark surface layers
- Use muted text color for secondary information

### 2. Typography
- **Headings:** Always use Poppins font (700-800 weight)
- **Body Text:** Always use Inter font (400-500 weight)
- Maintain size hierarchy:
  - H1: text-4xl sm:text-5xl (headings)
  - H2: text-2xl (subheadings)
  - Label: text-sm (form labels)
  - Body: text-base (general content)

### 3. Icons
- **Use Lucide Icons exclusively** for visual elements
- Size: h-5 w-5 for form fields, h-6 w-6 for buttons
- Color: text-muted for inputs, text-white for buttons
- Always initialize with `lucide.replace()` at the end

### 4. Responsive Design
- Mobile-first approach: design for mobile, enhance for larger screens
- Use Tailwind breakpoints:
  - `sm:` (640px) for tablets
  - `lg:` (1024px) for desktops
- Test layouts on all viewport sizes
- Use `max-w-4xl` for container max-width
- Maintain padding consistency: px-4 (mobile), sm:px-6, lg:px-8

### 5. Form Design
- **All inputs must have icons** for visual clarity
- Use consistent border color and styling
- Implement focus states with border-focus color change
- Add smooth transitions for all interactive elements
- Validate required fields with `required` attribute
- Provide clear error messages for validation failures
- Use rounded-3xl for border-radius consistency

### 6. Navigation & Links
- **Every authentication page must have a navigation link** to related pages
- Link styling: `text-white hover:text-focus font-medium`
- Separate navigation with border divider (border-t border-border)
- Add top padding to match spacing: `pt-6`
- Use descriptive link text (e.g., "Back to sign in", "Please sign up")

### 7. Buttons & CTAs
- **Primary buttons:** bg-[#DF6B33] hover:bg-[#c95c2c]
- **Secondary buttons:** bg-[#11141E] hover:bg-[#1D2032]
- Consistent padding: px-5 py-4 for full-width, px-4 py-3 for inline
- Full width on mobile/tablet for primary actions
- Font weight: font-semibold for buttons

### 8. Spacing & Layout
- Grid layout for multi-column pages: `grid gap-10 lg:grid-cols-[1.1fr_0.9fr]`
- Vertical spacing: `space-y-5` or `space-y-4` for form sections
- Margin between major sections: mt-6, mb-7
- Consistent padding in containers: p-7 sm:p-8

### 9. Feature Cards (Optional)
- Use 3-column grid on mobile: `sm:grid-cols-3`
- Styling: `rounded-3xl bg-[#0F111E] p-5 text-center shadow-lg shadow-black/20`
- Each card: title (text-2xl, bold) + description (text-sm, muted)

### 10. Accessibility
- Use semantic HTML: `<label>`, `<form>`, `<button>`
- Include `required` attribute for mandatory fields
- Use `type="email"`, `type="password"`, `type="tel"` for input validation
- Provide clear placeholder text
- Use focus states for keyboard navigation
- Ensure sufficient color contrast (white text on dark backgrounds)

---

## CSS Framework

### Framework
- **CSS Framework:** Tailwind CSS v3
- **CDN:** https://cdn.tailwindcss.com
- **Custom Configuration:** Defined in `<script>` with extended colors and fonts

### Tailwind Custom Config
```javascript
tailwind.config = {
  theme: {
    extend: {
      colors: {
        dark: '#090A14',
        surface: '#10121E',
        border: '#272A3C',
        focus: '#DF6B33',
        muted: '#8D93A1'
      },
      fontFamily: {
        sans: ['Inter', 'sans-serif'],
        display: ['Poppins', 'sans-serif']
      }
    }
  }
}
```

---

## Implementation Checklist for New Pages

- [ ] Use HTML5 semantic structure
- [ ] Import Google Fonts for Poppins and Inter
- [ ] Include Tailwind CSS CDN
- [ ] Configure Tailwind colors and fonts
- [ ] Set dark color-scheme in `:root`
- [ ] Use #090A14 as background
- [ ] Add Lucide Icons CDN and initialize with `lucide.replace()`
- [ ] Create responsive 2-column layout on desktop
- [ ] Implement mobile-first responsive design
- [ ] Use consistent color palette throughout
- [ ] Add all form icons (mail, lock, user, phone, etc.)
- [ ] Implement input validation (type, required, pattern)
- [ ] Add focus states on inputs (border-focus color)
- [ ] Include error messages for validation failures
- [ ] Add navigation links to related pages
- [ ] Test on mobile, tablet, and desktop
- [ ] Ensure all interactive elements have hover states
- [ ] Use consistent spacing and padding
- [ ] Apply smooth transitions to all interactive elements
- [ ] Validate HTML and CSS

---

## File Structure

```
workspace/
├── login.html       (Authentication page - Sign in)
├── register.html    (Authentication page - Sign up)
└── CLAUDE.md        (This documentation)
```

---

## Future Enhancements

1. **Password Reset Page** - Forgot password flow with email verification
2. **Email Verification Page** - Confirm email during registration
3. **Dashboard Page** - User profile and account settings
4. **Two-Factor Authentication** - Security enhancement
5. **Social Auth Integration** - Backend implementation for OAuth providers
6. **API Integration** - Connect forms to backend services

---

## Notes

- All pages are built with progressive enhancement in mind
- JavaScript validation runs client-side for better UX
- Server-side validation should always be implemented for security
- All form data should be encrypted during transmission (HTTPS)
- Consider implementing CSRF protection for production use
- Phone number validation allows exactly 10 digits
- Password confirmation validation uses JavaScript for real-time feedback
- Keep the dark theme throughout all authentication flows

---

**Last Updated:** June 1, 2026
**Status:** Active - Both login.html and register.html implemented
