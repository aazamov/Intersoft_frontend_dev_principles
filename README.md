# Intersoft tech Frontend development principles

## Folder Meaning

## Folder Structure

- `app/`  
  Application entry point: global providers, routing, and main app layout.

- `pages/`  
  Top-level page components. Only responsible for layout and composing widgets/features. No business logic.

- `entities/`  
  Core business models and logic (e.g. User, Product, Video). Contains types, state, and domain logic.

- `features/`  
  Focused, reusable units for a single user action or business process (e.g. login form, add to cart). Encapsulates UI + logic for that action.

- `widgets/`  
  Large, reusable UI blocks composed from features/entities (e.g. Header, Sidebar, CartWidget). Used to build pages.

- `shared/`  
  Universal, app-wide resources: UI components (buttons, inputs), hooks, helpers, constants, schemas, types, utilities, and libraries.

## Folder Rules

1. `pages/` should only handle routing and UI composition. No business logic here.
2. Place all universal, reusable resources (UI, hooks, helpers, constants, etc.) in `shared/`.
3. `entities/` contains domain models and their logic/state. Each entity = one business concept.
4. `features/` are small, focused units for a single user action or business process. One feature = one action.
5. `widgets/` are large, reusable UI blocks made from features/entities, used to compose pages.
6. Keep the folder structure flat. Avoid deep nesting to make things easy to find and maintain.

## General Coding rules.

1. Keep components small
2. Write reusable components in shared/ui
3. Move API calls to `(api)` folder
4. Write folder name fully and should be simple
5. Absolute imports `(@/components/xyz)` not `"../../../hell"`

## Naming rules

`Folders` = "kebab-case" (user-profile/)

`File` = "camelCase" (useUser.ts)

`Component` = "PascalCase" (LoginForm.tsx)

`Hook` = "use + PascalCase" (useLogin.tsx)

`Constants` = "UPPER_SNAKE_CASE" (API_BASE_URL)

`api-requests` = "kebab-case" (api/auth-requests.ts)

`api-hooks` = "kebab-case" (api/auth-hooks.ts)

`icons-file` = "kebab-case" (video-player-icons.tsx)

## Typescript

Use "DTO" for API types (LoginRequestDTO, UserResponseDTO)
Use "PascalCase" for interfaces and types (User, Product, CartItem)
Use "Props" for component props (LoginFormProps)
Use "T" prefix for generic reusable types (TOption, TColor)

## Styling

Tailwind css
Use "cn" for merging
Use this for Automatic Class Sorting "npm install -D prettier prettier-plugin-tailwindcss"
prettier config ``` {
"plugins": ["prettier-plugin-tailwindcss"]
}

````

## Example of using (icons)

Component name should start with "Icon"

```export interface IconProps extends SVGProps<SVGSVGElement> {}
    export const IconFacebook = (props?: IconProps) => (
      <svg {...props}> </svg>
    );
````

## General Packages

### State managers

1. Context API
2. Zustand

### Form

1. react-hook-form
2. zod for validation

### Requests

1. tanstack-query, + axios
2. use fetch in next js for ssr requests

### Localization

1. next-intl (next)
2. react-i18next (react)

### Date formatter

1. day.js

## Extensions for VScode

1. Prettier
2. Code spell checker

## examples of folder structure

```
src/
├── app/                            # App shell, routing, layouts
│   ├── layout.tsx
│   ├── page.tsx
│   └── providers/ThemeProvider.tsx

├── shared/                         # Reusable universal code
│   ├── ui/                         # Common UI elements
│   │   ├── Button.tsx
│   │   ├── Modal.tsx
│   │   └── Spinner.tsx
│   ├── hooks/
│   │   └── useDebounce.ts
│   ├── utils/
│   │   └── formatDate.ts
│   ├── constants/
│   │   └── api.ts
│   └── types/
│       └── common.ts

├── entities/
│   ├── user/
│   │   ├── model/useUser.ts
│   │   └── types.ts
│   ├── video/
│   │   ├── model/useVideo.ts
│   │   └── types.ts
│   ├── subscription/
│   │   └── model/useSubscription.ts
│   └── rating/
│       └── model/useRating.ts

├── features/                       # One action = One feature
│   ├── auth/
│   │   └── login-form/
│   ├── video/
│   │   ├── like-video/
│   │   ├── rate-video/
│   │   └── save-to-watchlist/
│   ├── user/
│   │   └── update-avatar/
│   └── search/
│       └── global-search-bar/

├── widgets/                        # Large UI blocks
│   ├── Header/
│   ├── Footer/
│   ├── VideoPlayer/
│   ├── AuthModal/
│   └── SearchOverlay/

├── processes/                      # Full user/business flows
│   ├── watch-video/
│   │   ├── ui/WatchLayout.tsx
│   │   ├── model/useWatchContext.ts
│   │   └── lib/initWatch.ts
│   ├── manage-subscription/
│   └── user-settings/

├── pages/
│   ├── index.tsx                   # Homepage
│   ├── watch/[id]/page.tsx        # Watch video page
│   ├── profile/page.tsx
│   └── settings/page.tsx

```

### shared

```
shared/
├── ui/
│   ├── Button/
│   ├── Modal/
│   ├── Avatar/
├── hooks/
│   ├── useDebounce.ts
│   ├── useClickOutside.ts
├── lib/
│   ├── formatDate.ts
│   ├── request.ts                   # axios base instance
├── config/
│   ├── api.ts
│   ├── auth.ts
├── types/
│   ├── pagination.ts
│   ├── api-response.ts

```

## widget

```
widgets/
├── Header/
│   ├── ui/Header.tsx
│   ├── model/useHeaderSearch.ts
├── Sidebar/
├── CartPreview/
├── UserDropdown/
├── VideoPlayer/

```

## features

```
features/
├── auth/
│   ├── login-form/
│   ├── logout-button/
├── organization/
│   ├── invite-member/
│   ├── switch-organization/
├── product/
│   ├── add-to-cart/
│   ├── rate-product/
├── file/
│   ├── upload-file/
│   ├── download-button/

```

## entities

```
entities/
├── user/
│   ├── model/useUser.ts
│   ├── types.ts
│   ├── api/userApi.ts
├── product/
│   ├── model/useProduct.ts
│   ├── lib/parsePrice.ts
│   ├── types.ts
├── organization/
│   ├── model/useOrganization.ts
│   ├── lib/canEditOrg.ts
├── file/
│   ├── model/useFileUpload.ts
│   ├── lib/getFileIcon.ts

```
