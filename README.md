<div align="center">
  <img src="./imgs/LOGO.png" alt="Black Brian logo" width="180" />

  <h1>Black Brian Automotive Studio</h1>

  <p><strong>A premium digital experience for automotive detailing, protection, and care.</strong></p>

  [![Website](https://img.shields.io/badge/Website-blackbrian.com.br-18181b?style=for-the-badge&logo=googlechrome&logoColor=white)](https://blackbrian.com.br)
  [![Vercel](https://img.shields.io/badge/Deployed_on-Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://vercel.com)
  [![Supabase](https://img.shields.io/badge/Data-Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)
  [![Tailwind CSS](https://img.shields.io/badge/UI-Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)

  [Live website](https://blackbrian.com.br) · [Service menu](https://blackbrian.com.br/Cardapio/Index.html) · [Automotive blog](https://blackbrian.com.br/blog)
</div>

---

## Overview

Black Brian is a responsive, multi-page web platform built for a premium automotive detailing studio in São João del-Rei, Brazil. It combines a polished business website with interactive sales tools, dedicated service experiences, content publishing, and internal scheduling.

The project is intentionally lightweight: its pages are built with vanilla web technologies and load their UI and integration libraries from CDNs, so there is no bundler or compilation step.

## Highlights

- **Premium storefront** — service presentation, customer reviews, studio location, social links, and direct conversion through WhatsApp.
- **Interactive service menu** — customizable detailing packages, optional treatments, automatic pricing, order summary, and WhatsApp checkout.
- **3D window-film configurator** — selectable vehicle models, paint colors, glass zones, film shades, product comparison, and a guided quotation flow.
- **Paintless dent repair showcase** — a dedicated *Martelinho de Ouro* landing page with video, before-and-after results, and quote CTAs.
- **PPF catalog** — focused paint-protection-film applications with individual WhatsApp booking links.
- **Dynamic automotive blog** — category-based posts, clean article URLs, social sharing, and content loaded from Supabase.
- **Content editor** — rich-text post creation with Quill, automatic slugs, image preview, and Supabase Storage uploads.
- **Internal scheduling** — monthly calendar with appointment creation, editing, filtering, and deletion backed by Supabase.
- **Marketing and discoverability** — responsive metadata, Open Graph tags, structured data, Google Analytics, Google Tag Manager, and Meta Pixel.

## Tech Stack

| Layer | Technologies |
| --- | --- |
| Structure | HTML5, semantic markup, multi-page architecture |
| Styling | Tailwind CSS via CDN, custom CSS, responsive design |
| Client logic | Vanilla JavaScript (ES6+), DOM APIs |
| Backend services | Supabase JavaScript SDK, PostgreSQL, Supabase Storage |
| 3D experience | Google `<model-viewer>`, GLB models, HDR environment lighting |
| Content editing | Quill rich-text editor |
| Icons and typography | Phosphor Icons, Google Fonts (Inter) |
| Conversion | WhatsApp deep links with generated order messages |
| Analytics | Google Analytics, Google Tag Manager, Meta Pixel |
| Hosting and routing | Vercel, clean blog URL rewrites |

## Platform Areas

| Path | Purpose |
| --- | --- |
| `/index.html` | Main institutional website and service overview |
| `/Cardapio/Index.html` | Interactive services, packages, pricing, and order summary |
| `/Peliculas_Solares/index.html` | 3D solar-film simulator and quotation wizard |
| `/Martelinho_de_Ouro/index.html` | Paintless dent repair landing page |
| `/PPF/index.html` | Paint protection film catalog |
| `/blog/index.html` | Dynamic blog listing |
| `/blog/post_view.html` | Dynamic article renderer used by clean blog routes |
| `/blog_panel.html` | Internal blog publishing interface |
| `/agenda_interna.html` | Internal appointment calendar |
| `/pdf.html` | Printable solar-film services presentation |

## Project Structure

```text
.
├── index.html                 # Main website
├── Cardapio/                  # Interactive service menu
├── Peliculas_Solares/         # 3D film configurator, models, and HDR assets
├── Martelinho_de_Ouro/        # Paintless dent repair experience
├── PPF/                       # Paint protection film catalog
├── blog/                      # Blog listing, articles, and images
├── blog_panel.html            # Blog editor
├── agenda_interna.html        # Appointment management
├── pdf.html                   # Printable film catalog
├── imgs/                      # Shared brand and page assets
└── vercel.json                # Clean blog URL rewrite
```

## Running Locally

No dependency installation or build command is required. Clone the repository and serve its root with any static HTTP server:

```bash
git clone <repository-url>
cd WebSite_BlackBrian
python -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000).

> Opening the HTML files directly with a `file://` URL is not recommended. An HTTP server provides behavior closer to production and avoids browser restrictions around assets and routes.

## Supabase Configuration

Supabase powers the dynamic blog, image uploads, and internal appointment calendar. The current front end expects:

- a `posts` table for blog content;
- an `agendamentos` table for appointments;
- an `imgs_blog` Storage bucket for article covers.

The public Supabase URL and anonymous key are currently declared in the pages that consume them. Before using a different project, replace those values in:

```text
blog/index.html
blog/post_view.html
blog_panel.html
agenda_interna.html
```

Because this is a client-side application, the anonymous key is public by design. Security must be enforced with appropriate Supabase Row Level Security and Storage policies. Internal management pages should also be protected before being exposed in a production environment.

## Deployment

The repository is ready for zero-build deployment on Vercel:

1. Import the repository into Vercel.
2. Keep the framework preset as **Other**.
3. Leave the build command and output directory unset.
4. Configure the production domain.

`vercel.json` rewrites URLs shaped like `/:category/:slug` to the dynamic article renderer, allowing shareable blog paths without duplicating HTML files.

## Customization Notes

- Brand colors are defined in each page's inline Tailwind configuration.
- Service names, prices, bundles, and selection rules live directly in the scripts inside `Cardapio/Index.html` and `Peliculas_Solares/index.html`.
- Vehicle assets use `.glb` models and an `.hdr` studio environment under `Peliculas_Solares/`.
- WhatsApp numbers and prefilled messages are declared in the relevant page scripts and links.
- Analytics identifiers are embedded in the public-facing pages and should be updated when deploying for another business.

## Browser Support

The experience targets current versions of Chrome, Edge, Firefox, and Safari. WebGL support is required for the 3D configurator; all other public areas use standard browser APIs and remain independent of the 3D viewer.

## License

No open-source license is currently included. All source code, visual assets, branding, and content remain the property of their respective owner unless stated otherwise.

---

<div align="center">
  <strong>Designed to turn automotive care into a premium digital journey.</strong>
  <br />
  Black Brian · São João del-Rei, Minas Gerais, Brazil
</div>
