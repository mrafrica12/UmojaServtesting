# Lash Lair case study — images

| File | What it shows |
|---|---|
| `lashlair-before.webp` / `-640.webp` | PageSpeed Insights, mobile, lashlair.com — report from 27 Sep 2026, 9:22 PM EDT: Performance 83, Accessibility 95, Best Practices 100, SEO 100; FCP 2.9 s, LCP 3.5 s, TBT 20 ms, CLS 0, SI 4.9 s |
| `lashlair-after.webp` / `-640.webp` | Same test, report from 27 Sep 2026, 10:02 PM EDT: Performance 98, Accessibility 95, Best Practices 100, SEO 100; FCP 1.5 s, LCP 2.2 s, TBT 0 ms, CLS 0, SI 2.1 s |

Both runs: Lighthouse 13.5.0, emulated Moto G Power, Slow 4G throttling. Unedited
captures, cropped only to the report area (from "Report from …" to the capture
footer) like the Rumi screenshots — the blank page margin and the PageSpeed
header bar were trimmed. Large files are 1200 px wide, `-640` files 640 px;
WebP q90, metadata stripped.

Source PNGs ("LashLairOpt Before.png", "LashLairIOpt After.png") are kept
outside the site in `UmojaServ/Image Originals/lash-lair-2026-09-27/`.
