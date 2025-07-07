# Architecture

Using FSD

Folder Meaning

`app/` Entry setup: providers, routing, app layout  
 `shared/` Shared stuff: buttons, inputs, constants, helpers, hooks, schemas  
 `entities/` Basic business models (User, Product, Video) with data & logic  
 `features/` Small pieces of logic/actions (e.g. login form, add to cart button)
`widgets/` Ready UI blocks that show on pages (e.g. CartWidget, Header)  
 `processes/` Full business flows (e.g. checkout, registration)  
 `pages/` Page components with layout and widget composition only

Folder Rules

1. No business logic in pages. Pages are only for routing and UI composition.
2. Use shared/ for universal things. Buttons, helpers, configs = put them in shared/.
3. entities/ hold core logic about the domain. Like: user, product, video.
4. features/ are small interactive logic units. One feature = one user action (e.g. login, like post, add to cart).
5. widgets/ are big reusable parts for layout. Like: Header, Sidebar, VideoPlayer.
6. Keep structure flat, not deep. Avoid nesting too deep; keep things easy to find.

General Coding rules.

1. Keep components small
2. Write reusable components in shared/ui
3. Move API calls to (api) folder
4. Write folder name fully and should be simple
5. Absolute imports (@/components/xyz) not "../../../hell"

Naming rules
Folders = "kebab-case" (user-profile/)
File = "camelCase" (useUser.ts)
Component = "PascalCase" (LoginForm.tsx)
Hook = "use + PascalCase" (useLogin.tsx)
Constants = "UPPER_SNAKE_CASE" (API_BASE_URL)
api-requests = "kebab-case" (api/auth-requests.ts)
api-hooks = "kebab-case" (api/auth-hooks.ts)
icons-file = "kebab-case" (video-player-icons.tsx)

Typescript
Use "DTO" for API types (LoginRequestDTO, UserResponseDTO)
Use "PascalCase" for interfaces and types (User, Product, CartItem)
Use "Props" for component props (LoginFormProps)
Use "T" prefix for generic reusable types (TOption, TColor)

Styling
Tailwind css
use "cn" for merging
use this for Automatic Class Sorting "npm install -D prettier prettier-plugin-tailwindcss"

Example of using (icons)
Component name should start with "Icon"
export interface IconProps extends SVGProps<SVGSVGElement> {}
export const IconFacebook = (props?: IconProps) => (
<svg {...props}> </svg>
);

packages
State managers
Context API
Zustand

Form
react-hook-form
zod for validation

requests
tanstack-query, + axios
use fetch in next js for ssr requests

localization
next-intl (next)
react-i18next (react)

Date formatter
day.js

Extensions for VScode
Prettier
Code spell checker
