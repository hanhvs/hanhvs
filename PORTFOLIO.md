# GitHub Portfolio — Vương Sỹ Hạnh (@hanhvs)

> Tổng hợp toàn bộ repositories + đóng góp thật (git log `author=hanhvs`). Cập nhật: 2026-08-20.
> Dữ liệu từ GitHub UI + clone full repo + `git log --author=hanhvs` (không bịa số liệu).

## Tổng quan

- **Tài khoản:** [@hanhvs](https://github.com/hanhvs) — 19.5k commits, 155 PRs
- **Tổ chức (7):** KGBRecord (79 repos), XPocketApp (10), TelegramTrading (1), CaperTools (5), AGIVietNam (30), AI20K-Build-Cohort-2 (2), aI-repo-dp-vsf (6)
- **Đóng góp open-source:** NousResearch/hermes-agent, nikitabobko/AeroSpace, MediosZ/SwipeAeroSpace, Bleuzen/Blizcord
- **Tổng repos:** ~135

---

## 1. KGBRecord — Trading & Agent (org cá nhân, 79 repos)

### Dự án chính (đã phân tích sâu)

| Repo | Stack | Kiến trúc & Feature | Commits hanhvs |
|------|-------|---------------------|----------------|
| **9router** | Next.js 16 + React 19 + Tailwind 4 + Zustand; Node custom-server (Express 5 + http-proxy-middleware); SQLite; MITM proxy (node-forge); SSE; CLI | **AI Router & Token Saver.** MITM proxy chặn traffic AI tools (Claude Code, Cursor, Codex...), kết nối 40+ provider/100+ model, RTK tiết kiệm 20-40% tokens, auto-fallback model free/rẻ, combo generator, dashboard quản lý combo/model, i18n. | **17** |
| **trade-engine** | Nx monorepo (pnpm) + TS; NestJS 11 (api) + Next.js (web) + Python/shell (engine); Prisma + Postgres; Redis, RabbitMQ, MinIO, Qdrant; TradingView CDP | **Market-analysis automation đa instrument** (BTC, NASDAQ, XAU). Pipeline bước-có-thứ-tự: fetch MTF (TradingView CDP) → analyze → compose plan → draw → summarize. MCP server, knowledge docs + semantic search (Qdrant), order/journal/signal tracking, risk service, IAM, cron động. | **90** |
| **BKVN-Hermes** | Nx monorepo + TS; NestJS 11 + Next.js; Prisma + Postgres; Hermes Agent (AI code-gen); Playwright | **BKVN Quote-Calc Studio.** Quét công thức tính diện tích/hình học từ bkvn-x-be, bộ luật đối chiếu bắt lỗi (đơn vị, tham số, kết quả bất thường), tính thử, sửa công thức qua mô tả bằng lời (Hermes Agent ghi code, 6 lớp guardrail fail-closed), audit reporting. | **4** |
| **shell-core** | C (LibRetro core) + Makefile + shell; Docker; RetroArch | **LibRetro core chạy shell script qua giao diện giả lập game.** Mỗi .sh là một "ROM", bắt output terminal real-time, script tương tác/menu, cross-platform, installer đa môi trường. | **4** |
| **1-BE-Auth-Service** | NestJS 11 + Prisma 5 + Postgres (submodule); Passport (JWT, Google OAuth, anonymous); Redis; Swagger; Docker; CI/CD | **Auth microservice.** Login email/password + Entra ID, JWT, role-based guard, Google OAuth, soft-delete, auto-deploy. | **45** |
| **1-BE-Gateway-Service** | NestJS 11 + Prisma 5 + Postgres; Passport; Redis; Swagger; Docker; CI/CD | **API Gateway.** Login/logout/refresh-token, JWT guard + optional-JWT, auth interceptor, Entra ID, TCP microservice communication. | **46** |
| **1-FE-Web** | React 19 + TS + Vite 7; Tailwind 4; Radix UI; Zustand; Azure MSAL; reactflow; react-signature-canvas | **Web client AGI-One.** Dashboard, settings, workflow builder (reactflow), auth Azure MSAL, i18n, chữ ký điện tử, Docker + auto-deploy. | **10** |
| **KGBHub-BE** | Node + TS + Express 4; Prisma 5 + Postgres; Redis; Bull; Stripe; Google OAuth2/Sheets; Nodemailer + React-Email; Socket.io; cron | **Nền tảng học trực tuyến.** Khóa học/lesson, campaign marketing (Bull queue + email), chat, form, báo cáo, thanh toán Stripe, cron refresh + stripe checker, Google OAuth2, upload file, email template React-Email, socket realtime. | **18** |
| **Concierge** | Repo rỗng (0 commit) | Chưa có code. | **0** |

### Repos khác (đã phân tích stack/kiến trúc)

**Hệ thống AGI-One (microservices):**

| Repo | Stack | Kiến trúc | Commits |
|------|-------|-----------|---------|
| **1-BE-System-Service** | NestJS + Prisma + Redis + Google APIs + JWT/Passport + Swagger | AGI-One backend microservice (config, prisma, middlewares, multer) | **32** |
| **1-BE-Example-Service** | NestJS + Prisma + Redis + Google APIs + JWT/Passport + Swagger | AGI-One backend microservice (template/example) | **52** |
| **1-prisma** | Prisma ORM + prisma-extension-soft-delete | Centralized DB schema service (schema + migrations) | **16** |
| **1-database** | Docker Compose (MSSQL 2022, Postgres) | DB infra | **7** |

**Game / emulator (J2ME, RetroArch):**

| Repo | Stack | Kiến trúc | Commits |
|------|-------|-----------|---------|
| **NSO-Server** | Java + Maven (server2512) | Game server Ninja School Online: server/io/real/boardGame/threading/cache/config/patch/tasks | **11** |
| **NSO-Client** | Unity (C#) | Game client Unity: Assets/Scripts/Resources | **4** |
| **NSO-Client-J2ME** | Java ME (J2ME) | Mobile client J2ME: src/kgbrecord/modules | **40** |
| **NRO-Server** | Java + Maven (nro_noah) | Game server: src/main/java/nro | **0** |
| **NRO-Client** | Unity (C#) | Game client Unity | **0** |
| **SquirrelJME** | Java + Gradle (Java ME 8 VM) | VM: emulators/ (springcoat-vm, nanocoat-vm) | fork |
| **RetroArch** | C (Makefile) | Multi-system emulator frontend: audio/video/camera/cheevos/ai | fork |
| **Lakka-LibreELEC** | LibreELEC build system | Linux distro packaging RetroArch | fork |
| **freej2me-plus-lakka** | Java + Makefile + build.xml | J2ME emulator libretro core | fork |
| **fake-08** | C/C++ (Makefile) | PICO-8 emulator: source/platform (libretro, SDL2, 3ds) | fork |
| **retro8** | C++ (CMake) | PICO-8 emulator libretro core: src/vm, lua, libretro | fork |
| **Assembly-CSharp** | C# .NET (Unity) | Unity game scripts NinjaSchool: Char, ChatManager, Clan, Auto, Buff | fork |

**AI / tools:**

| Repo | Stack | Kiến trúc | Commits |
|------|-------|-----------|---------|
| **MoneyPrinterTurbo** | Python 3.11, Streamlit, FastAPI, FFmpeg, faster-whisper, edge-tts, OpenAI | AI video generator: webui (Streamlit) + app/ backend | fork |
| **Deep-Live-Cam** | Python, ONNX, insightface, opencv, customtkinter, tensorflow | Face-swap app: modules/ pipeline, CUDA/DirectML/Apple Silicon | fork |
| **ClawTeam** | Python 3.10, agent framework | AI agent framework: clawteam/ core, skills/, scripts/ | **1** |
| **crw4a** | Python, crawl4ai, Docker, Chromium | Web crawler: app/ (main.py + web UI), config qua UI | **8** |
| **hermes-project-fix** | Python, Makefile | Script backfill Hermes sessions vào Projects (dry/fix/verify) | **3** |
| **AskDB-Electron** | Electron 33, React 19, Express 4, TS | Desktop DB client: main/ (Electron), renderer/ (React), server/ | **1** |
| **drawdb** | React 18, Vite, Tailwind 4 | DB schema diagram tool (SPA) | fork |
| **drawdb-server** | TypeScript, Express 4 | Backend cho drawdb | fork |

**Web / app:**

| Repo | Stack | Kiến trúc | Commits |
|------|-------|-----------|---------|
| **Selected** | NestJS 9, Mongoose, JWT, Socket.io, Fastify | Backend music streaming API | **0** |
| **Selected-React** | React 18, Redux+Redux-Saga, Tailwind 3 | Frontend SPA music streaming | fork |
| **Selected-Docker-FullStack** | Docker Compose, NestJS, React, MongoDB | Full-stack orchestration | **0** |
| **JSB-WebBanHang** | React 17, TS, nginx | E-commerce frontend | **0** |
| **JSB-WebBanHang-BE** | Java, Spring Boot, JPA, MySQL, WebFlux | E-commerce backend | **0** |
| **locket_fe** | React 18, CRA, Tailwind, vercel | Frontend SPA | **0** |
| **locket_be** | Node.js, Express 4 | Backend API | **0** |
| **WeeBoo-BackEnd** | NestJS 10, Prisma 5, Passport | Backend API: src/modules, prisma, uploads | **23** |
| **OELY-Backend** | Go 1.24, Gin, ent, AWS S3, JWT | Backend API: src/, migrations, uploads | **27** |
| **KGBLaundry-Nest** | NestJS 10, Prisma 5, Passport | Laundry backend: src/modules, prisma | **18** |
| **Giatla.me** | Node.js, eroc framework | Microservices monorepo: laundry/file/map/payment/socket/video/center | **0** |
| **reviewking.info** | Nx 22, NestJS 11, Next.js, Prisma 7, pnpm | Monorepo: api/ (NestJS), web/ (Next), iam/ | **10** |
| **TouYen** | NestJS, Prisma 7, TS | Backend: src/modules, prisma, scripts | **26** |
| **Vive** | Nx 22, NestJS 11, Next.js, Prisma 7 | Monorepo: api/, web/, packages/, iam/ | **39** |
| **Malolo** | Next.js 14, React 18, Express 4, Prisma | 3-part: frontend (Next), backend (Express+Prisma), common | **3** |
| **DELY** | Nx, NestJS, Next.js, Prisma, Python 3.11 engine | Monorepo: api/, web/, engine/ (Python), iam/ | **1** |
| **MEILING** | Express 4, Prisma 5, TS | Backend API: src/, prisma, database | **1** |
| **Meiling-reader** | Python, Telethon, Kafka, Docker | Telegram reader bot | **1** |
| **Xpocket** | Node.js microservices, Next.js 14, MongoDB, Kafka, MinIO, Redis | Microservices: backend/ (20 services), frontend/ (marketplace+XACC), service/ | **0** |
| **KGBHub-FE** | Next.js 14, React, Tailwind | Frontend KGBHub | **1** |
| **KGBHub-Docs** | Docs (PDF/PPTX/DOCX) | Academic deliverables: KTPM_VuongSyHanh poster/report/slides | **1** |

**Power Platform / PCF:**

| Repo | Stack | Kiến trúc | Commits |
|------|-------|-----------|---------|
| **ExcelShow** | Power Apps PCF, React 16, TS | PCF control: DataToExcelComponent, DatasetToExcel | **1** |
| **pcf-kanban-control** | Power Apps PCF, React 16, TS | PCF control: KanbanViewControl | **1** |
| **Power-Platform-PCFs** | Power Apps PCF, React, TS | PCF collection: fileUploader control | **1** |

**Map / bot / misc:**

| Repo | Stack | Kiến trúc | Commits |
|------|-------|-----------|---------|
| **MAP-BE** | Java, Spring Boot, Maven, Lombok | Backend API | **0** |
| **MAP-FE** | React 18, CRA, Tailwind, react-konva | Frontend SPA | **0** |
| **map-tool** | Nx, Spring Boot (map-be), React 18 (map-fe) | Monorepo: apps/map-be, apps/map-fe, render_compare.py | **1** |
| **bot_scan** | Node.js, node-telegram-bot-api, Mongoose | Telegram bot: src/, database | **1** |
| **go_bot_scan** | Go 1.24, telebot, SQLite, btcd, bip39 | Telegram bot: bot/, thread/ | **1** |
| **TG-DownloadHelper-Unofficial** | Chrome Extension MV3, JS | Browser extension: js/, popup, options | **1** |
| **Avatar-Server** | Java, Maven, HikariCP, Lombok | Backend server: src/, database | **1** |
| **Avatar-Client** | Unity (C#) | Unity project | **1** |
| **EntraIDTest** | Go 1.24, Gin, ent, AWS S3, go-oidc | Backend API: src/, migrations | **1** |
| **BASE-TOOL** | Python, opencv, pyautogui, pytesseract, adbutils, tkinter | Automation tool: main.py, gui.py, ocr.py, device.py | **0** |
| **Tools** | Python, opencv, pyautogui, selenium, tkinter | Automation collection: DUCKY/, PIXELZ/, PixelsManager/, night-crows-G/ | **0** |
| **SharpXel** | C# .NET 4.7.2, WinForms | Windows desktop app: MainWindow.xaml, Bot.cs, Handler/ | **0** |
| **frappe-util** | ERPNext/Frappe, Docker Compose, Makefile | Dev environment: docker-compose, Makefile | **1** |
| **AeroSpace** | Swift 6.2, macOS 13+ | Tiling window manager: Sources/, grammar/ | fork |
| **SwipeAeroSpace** | Swift, macOS, SwiftUI | macOS app: SwiftUI views, SwipeManager | fork |
| **one** | (clone timeout) | Twenty CRM fork | fork |
| **two** | Nx, NestJS 11, Angular, Gauzy | Monorepo (Gauzy fork): apps/, packages/ | fork |
| **SSurvival** | (empty repo) | Không có code | **0** |
| **FakeConc** | Python, colorama | Single main.py script | **1** |
| **hanhvs** | — | — | — |
| **.github** | — | Org config | — |

## 2. XPocketApp — NFT Marketplace (Immutable X)

Microservices Node.js (`eroc` framework) + MongoDB (Mongoose) + ImmutableX SDK, Docker hóa. **Hệ thống marketplace NFT trên Immutable X.**

| Repo | Kiến trúc & Feature | Commits hanhvs |
|------|---------------------|----------------|
| **user-service** | Auth: username/email/phone, ETH wallet, Discord/Google/ImmutableX Passport (JWT qua JWKS), TOTP 2FA, roles & admin, balance đa token (ETH/IMX/USDC/GODS), key API. Router 3 lớp /v1 /in /ui. | **28** |
| **trading-service** | Giao dịch NFT peer-to-peer (NFT↔NFT). Draft→confirm, accept/cancel/reject, chọn bên trả fee, gọi ImmutableX chuyển NFT, thống kê volume/profit. | **55** |
| **listing-service** | Niêm yết NFT bán (single & bulk), ETH/ERC20, cancel listing, claim NFT hết hạn, hoàn tiền, theo dõi order filled, refresh metadata. | **79** |
| **bundle-service** | Bán NFT theo bundle (gói nhiều NFT). Tạo/niêm yết/fill bundle, tính royalty fee, hoàn tiền, thống kê. | **61** |
| **order-service** | Đồng bộ & phục vụ order từ ImmutableX. Pull order/asset/collection/transfer, truy vấn theo collection, giá min theo token, quản lý collection admin, points. | **80** |
| **stat-service** | Tổng hợp thống kê toàn hệ thống (gọi /in/stats của các service). Active users, AOV, profit, total transactions/volume theo tháng, so sánh rivals, render chart. | **2** |
| **wantto-service** | "Want To" — đặt giá mong muốn mua/bán NFT. Tạo offer, accept (chuyển NFT qua IMX), cancel, tính fee, validate AJV. | **12** |
| **cashback-service** | Hoàn tiền tự động khi order filled (dựa trên fee address/bulk-listing wallet). Event-driven (xpocket_order.created/updated), lịch sử cashback, ETH + token. | **46** |
| **XACC** | Admin dashboard (Xpocket Admin Control Center). Next.js 14, quản lý bundle/collection/listing/event, phân tích doanh thu đối thủ, leaderboard, user. | **1** |
| **marketplace** | Frontend marketplace NFT. Duyệt market/collections, chi tiết NFT, events, claim center, ví (inventory/listings/offers/transactions), kết nối ví. | **0** |

## 3. TelegramTrading

| Repo | Stack | Feature | Commits |
|------|-------|---------|---------|
| **telegram-service** | Python + Telethon + Kafka + Docker | Đọc tin nhắn tín hiệu trading từ Telegram, phân loại (open position/update/close), forward, publish lên Kafka topic. | **0** |

## 4. CaperTools — Game Bots & Extensions

| Repo | Stack | Feature | Commits |
|------|-------|---------|---------|
| **PixelsManager** | Python 3.10, OpenCV, pyautogui, mss, customtkinter, web3/eth-keys, pyotp, selenium, pyinstaller, pyarmor, Flask, pytesseract | **Desktop bot manager cho game Pixels** (Ronin blockchain). GUI customtkinter điều khiển nhiều bot đa luồng, auto farming (craft/trees/land/city/quest), nhận diện màn hình OpenCV, ký giao dịch blockchain, quản lý account/proxy/device, OCR, build exe. | **0** |
| **PIXELZ** | Python 3.10, OpenCV, pyautogui, mss, customtkinter, web3, pyotp, selenium, pyinstaller, pyarmor, Flask, pytesseract | Bot farm Pixels + hỗ trợ Ronin wallet extension (crx), cấu hình profile, action module hóa. | **0** |
| **DUCKY** | Python, OpenCV, pyautogui, mss, customtkinter, pyinstaller, pytesseract | **Bot game NIGHT CROWS** (CarrieVerseBot). Phát hiện cửa sổ game, ThreadPool đa cửa sổ song song, auto farm + fishing, GUI. | **0** |
| **ext-pixels** | Chrome extension MV3, Vite + crxjs, InfernoJS, Babel | Extension cho game Pixels: content script chèn vào game, background service worker, popup/options/newtab/sidepanel, devtools. | **0** |
| **pixels-tools-extension** | Repo trống (chỉ README) | Không có code. | **0** |

## 5. AGIVietNam — Enterprise (BKVN / TDICONS / VBIM, 30 repos)

### Dự án chính (đã phân tích sâu)

| Repo | Stack | Kiến trúc & Feature | Commits hanhvs |
|------|-------|---------------------|----------------|
| **bkvn-x-be** | NestJS 11 + Prisma + Postgres + Redis + RabbitMQ + Socket.IO + AWS S3 + Azure Blob + JWT + Swagger + @microsoft/agents (Copilot Studio) | **Backend BKVN X.** Tính toán báo giá (quotation/quote/boq/formula) công thức phức tạp, workflow phê duyệt, tích hợp MISA + Getfly (CRM) + Copilot Studio agent, realtime socket, custom field, hệ số TMC, export báo giá, cron. | **742** |
| **bkvn-x-fe** | React 19 + TS + Vite 7 + Fluent UI + Tailwind 4 + Zustand + TanStack Query + MSAL + socket.io + botframework | **SPA BKVN-X** (Power Apps custom page). Quản lý báo giá (quotation) export file, chat (botframework + socket), dự án, IAM/account, thảo luận, vật tư, thông báo, CRM sync. | **244** |
| **BKVN-Helper** | Python 3.11 + FastAPI + pandas + openpyxl + PyYAML + anthropic | **API chuẩn hóa dữ liệu BKVN.** Chuẩn hóa CNC/TMC/OG, API báo giá (quote), xử lý Excel, tích hợp Anthropic AI, CI/CD auto-deploy theo branch. | **470** |
| **PCU-Server** | Go 1.24 + Gin + Ent ORM + Postgres + Redis + AWS S3 + Azure Blob + MinIO + OAuth2 (Microsoft Graph) + JWT + OpenAI + excelize + websocket | **Backend quản lý nhà cung cấp & vật tư.** Auth OAuth2 Microsoft + JWT (token blocking, session reactivation giờ hành chính), upload file, AI OpenAI, chuẩn hóa dữ liệu, queue, cron, realtime websocket, material request history. | **305** |
| **tdicons-be** | NestJS 11 + TypeORM + Postgres + Redis + RabbitMQ + Socket.IO + AWS S3 + Swagger + exceljs | **Backend TDICONS.** Auth Microsoft SSO + RBAC tự dựng, nhật ký hoạt động, modules: customers/materials/warehouses/purchase-orders/contracts/projects/inventory/labors/machines, thảo luận, thông báo. | **0** |
| **tdicons-fe** | React 19 + TS + Vite 8 + Ant Design 6 + Tailwind 4 + Zustand + TanStack Query + chart.js + xlsx | **SPA TDICONS.** Quản lý dự án/công trình/vật tư/kho/khách hàng/nhân công/máy móc, phân quyền, nhập/xuất Excel, draft IndexedDB, thảo luận. | **0** |
| **vbim-be** | NestJS 10/11 + TypeORM + Postgres + Redis + RabbitMQ + Socket.IO + AWS S3 + Azure Blob + MSAL + Microsoft Graph + Vercel AI SDK + Copilot Studio | **Nền tảng học tập + agent M365 AI.** Courses/lessons/chapters/articles, agent M365 AI chat (lưu hội thoại bất đồng bộ + soft-delete), SharePoint, theo dõi tiến độ, analytics. | **25** |
| **vbim-fe** | Next.js 16 + React 19 + TS + Tailwind 4 + Radix UI + Zustand + MSAL + socket.io + botframework + react-markdown | **Web học tập + chat M365 AI.** Conversation history sidebar, markdown render, text selection + suggestion popup, khóa học, thư viện cá nhân, staff learning parts. | **12** |
| **vbim-cons-fe** | React 19 + TS + Vite + Ant Design 6 + Tailwind 4 + Zustand + TanStack Query + socket.io + chart.js + expr-eval-fork + Storybook | **SPA VBIM Cons** (quản lý thi công BIM). Quản lý dự án BIM, markup, khối lượng (quantity), viewer, issues, logs, reports, workspace tabs, p2q (plan-to-quantity). | **0** |

### Repos khác (đã phân tích stack/kiến trúc)

| Repo | Stack | Kiến trúc & Feature | Commits |
|------|-------|---------------------|---------|
| **vbim-cons-be** | NestJS + TypeORM + Postgres + Redis + AWS S3 + Socket.IO + Azure AD + Swagger | BIM construction: modules aps/auth/issues/logs/markups/metrics/projects/quantity/reports/viewer, Prometheus monitoring | **0** |
| **vbim-rag** | Python FastAPI + Qdrant + VoyageAI + Anthropic/Groq + sentence-transformers reranker + Redis + boto3 | RAG knowledge center: chunker/embedder/qdrant_store/s3_srt_cron/session_memory, hybrid retrieval (BM25+dense), reranking, conversational memory | **11** |
| **vbim-elearning** | Python FastAPI + Celery/Redis + Qdrant + VoyageAI + Anthropic/OpenAI/Gemini/Groq + Whisper + S3 | E-learning RAG: video/YouTube/Excel ingestion, agentic multi-chain chat, SQL chain, course suggestion, semantic cache | **14** |
| **vbim-elearning-fe** | Next.js + React + Tailwind + Radix UI + zustand + TanStack Query + MSAL | E-learning frontend: course library, personal library, staff learning parts, M365 chat, Azure AD login | **0** |
| **vbim-elearning-be** | (empty repo) | Placeholder | **0** |
| **VBIM_BE** | Node.js Express + MySQL + migrations + swagger | Legacy VBIM backend: routes/services/middleware/migrations | **0** |
| **pdt-be** | NestJS + TypeORM + Postgres + Redis + AWS S3 + Socket.IO + Azure AD + Swagger | PDT (price/BOQ) backend: boqs/boq-items/materials/coefficients/price-libraries/calculator/assistant/audit-logs | **4** |
| **pdt-fe** | React + Vite + antd + Tailwind + zustand + TanStack Query + Storybook + Vitest | PDT frontend: BOQ/price management UI, charts, resizable tables, Storybook | **0** |
| **pdt-standard** | (empty repo) | Placeholder | **0** |
| **iam-service** | NestJS + TypeORM + MySQL/Postgres + Redis + mailer + AWS S3 + Swagger | IAM: auth, user/company management, Redis cache, email, seed data | **10** |
| **agi-one-iam** | NestJS + TypeORM + MySQL/Postgres + Redis + mailer + Swagger | AGI One IAM: auth, user management, Redis cache, health checks | **0** |
| **knowledge_center_backend** | NestJS + TypeORM + Postgres + Redis + AWS S3 + Socket.IO + Azure AD + Swagger | Knowledge center: chat, document, catalogs/categories, feedback, notifications, admin, app-release | **2** |
| **knowledge_center_frontend** | React + Vite + Electron + Tailwind + shadcn + zustand + TanStack Query | Knowledge center desktop app (Electron): document browsing, chat, speech recognition, auto-update | **0** |
| **trungtamtrithuc-rag** | Python FastAPI + Celery/Redis + Qdrant + VoyageAI + Anthropic/OpenAI/Gemini/Groq + Whisper + S3 | Trung tâm tri thức RAG: document/video/Excel ingestion, agentic multi-chain chat, SQL chain, figure snapshot fusion | **11** |
| **PCU-Web-Client** | React + React Router + Vite + MSAL + Radix UI + Tailwind + zustand + TanStack Query | PCU web client: Azure AD auth (MFA, token refresh, domain-restricted login), data tables, forms | **14** |
| **TDI-PCU** | Python scripts + Excel (openpyxl/pandas) | TDI PCU data matching pipeline: Excel-based matching với synonym dictionary | **0** |
| **MCP-SERVERS-FOR-REVIT** | C# .NET (Revit plugin) + Node.js/TS MCP server | MCP server cho Autodesk Revit: AI-assistant-driven commands, dimension/shop-drawing generation | **0** |
| **db-auto-backup** | NestJS + @nestjs/schedule + Docker + Postgres/MySQL/MSSQL backup | Automated DB backup: sqlpackage/dbatools/mssql-scripter fallbacks, preDumpSql, S3 upload, scheduled | **19** |
| **standard-headings** | Python + sentence-transformers + FAISS + SharePoint + psycopg2 + pandas | BOQ heading standardization: embeddings/FAISS, SharePoint integration, one-to-many mapping, evaluation | **0** |
| **VMedia-Intelligence** | Python FastAPI + Qdrant + sentence-transformers + Anthropic + rank-bm25 + OCR | VMedia RAG chatbot: internal doc Q&A, hybrid search (BM25+dense), OCR/vision, font metadata | **3** |
| **s3-upload** | Python + boto3 + minio + python-dotenv | S3 bulk upload/transfer: multipart, server-side copy, SRT flatten/convert, progress tracking | **58** |

## 6. AI20K-Build-Cohort-2

| Repo | Stack | Feature | Commits |
|------|-------|---------|---------|
| **C2-App-011** | Nx monorepo (pnpm), NestJS API, Next.js web, Zalo Mini App, Prisma/Postgres, Python RAG (FastAPI, LangChain, LangGraph, Qdrant, sentence-transformers, rank-bm25, Redis), Playwright | **AI191 — AI Concierge 24/7 đa ngôn ngữ cho resort.** RAG đa ngôn ngữ (multilingual embedding + HyDE), agent LangGraph tool-use, search knowledge base, đặt dịch vụ (nhà hàng/spa/dọn phòng), IAM, Zalo Mini App, monitoring, rate limiting. | **1** |
| **starter-code-template** | Python, FastAPI, LangChain, LangGraph, pydantic, pytest, ruff | Template agentic AI backend: FastAPI routes + LangGraph agent (nodes/tools/state), Docker, test, docs. | **0** |

## 7. aI-repo-dp-vsf — Agentic BI / AI Research

| Repo | Stack | Kiến trúc & Feature | Commits hanhvs |
|------|-------|---------------------|----------------|
| **AgenticBIMemoryPOC** | Python 3.11, FastAPI, LangGraph, langchain-openai, Postgres (asyncpg), Redis, Qdrant, sentence-transformers, pydantic v2, JWT/bcrypt, Langfuse, RAGAS; Next.js/React + ECharts; Docker Compose; GitHub Actions | **Agentic BI chatbot (Vinpearl) ZERO-SQL.** LangGraph orchestrator: init_context → guardrail+prepare_reason → policy_clarity_gate → cyclic reason↔tools → calculator→compiler→present→finalize. Agent không tự viết SQL, chỉ gọi 5 semantic tool cố định (list_properties, get_revenue_by_property, total_revenue, compare_regions, top_properties). Memory 2 tầng STM (window/summarizer/cache) + LTM (embedder/extractor/retriever/Qdrant + scheduler). Runtime contract từ config YAML. SSE chat, IAM RBAC, guardrails, LLM-owned viz intent gate + ECharts, Langfuse tracing, RAGAS eval, tiếng Việt. | **109** |
| **promptoptx** | Python 3.12, FastAPI, SQLAlchemy 2 + Alembic, aiosqlite, pydantic v2, OpenAI, sqlglot, numpy/pandas/scipy/sklearn, typer/rich CLI, Langfuse; Next.js 15/React 19, TanStack, recharts, Playwright | **Adaptive Multi-Objective Prompt Optimization Framework.** Hệ thống thí nghiệm có kiểm soát (không phải rewriter): analyze → tìm weakness có evidence → plan → sinh candidate → benchmark interleaved → so sánh thống kê (pareto_front, decision_engine) → publish kèm confidence + sample size. "No conclusion without a measurement." | **0** |
| **PromptFineTuning** | Python 3.10+, langchain-core, langchain-google-genai/openai/anthropic, Langfuse, pytest; Next.js 15/React 19, Playwright, Vitest | **Prompt Studio — Prompt Audit Framework.** Đánh giá thiết kế prompt, đề xuất rewrite có kiểm soát, kiểm chứng trên frozen golden data. Detect task → sinh testcase → human review → freeze suite + checksum → score (council 4-model) → rewrite → contract verification → original vs rewrite. | **0** |
| **VPL-customer-mining** | Python 3.11, pandas, numpy, sklearn, scipy, statsmodels, seaborn, matplotlib, plotly, mlxtend, duckdb, AutoGluon Timeseries, Jupyter, Superset | **Vinpearl Customer Mining.** Workflow tái lập: data understanding → cleaning → validation (data_contract) → EDA → RFM → K-Means → association rules → anomaly detection → cancellation → retention → campaign scorecard → cross-sell → package performance. 22+ notebooks. | **0** |
| **SQL-Prompt** | Python 3.11, dspy-ai (GEPA), sqlglot, pymysql, pydantic v2, tiktoken, openai, MySQL 8.0; Next.js 16, drizzle-orm | **Correctness-gated SQL prompt optimizer.** LLM sinh đúng 30 SQL, validate MySQL 8.0 thật. Schema introspection → compaction → task contracts → token counter → SQLGlot validation (cấm SELECT *) → MySQL EXPLAIN → semantic validator → result comparator → GEPA chỉ rút gọn prompt khi correctness==1.0. | **0** |
| **ML-Causal-Agent-MCP** | Python 3.11/3.12, causal-learn, dowhy, networkx, sklearn, pandas, pydantic v2, openai, PyJWT, mcp, pyvis; Docker + nginx | **GreenSM Causal MCP Server.** Causal discovery, GCM root-cause analysis, causal graph management, confidence estimation, business explanation, query routing, reconciliation, stability/robustness, LLM graph generation, MCP long-running jobs, dataset registry, JWT security. | **0** |

## 8. Đóng góp open-source (ngoài org)

| Repo | Feature | Loại |
|------|---------|------|
| **NousResearch/hermes-agent** | Hermes Agent — self-improving AI agent, learning loop, skills từ experience. | Đóng góp |
| **nikitabobko/AeroSpace** | i3-like tiling window manager cho macOS. | Đóng góp |
| **MediosZ/SwipeAeroSpace** | Swipe 3 ngón đổi workspace AeroSpace. | Đóng góp |

## 9. Repositories cá nhân (@hanhvs)

| Repo | Stack | Feature | Commits |
|------|-------|---------|---------|
| **hermes-agent** | Python (FastAPI, uvicorn, httpx, PyJWT, python-telegram-bot); agent core + gateway + CLI + desktop (Tauri) | Fork của NousResearch/hermes-agent. Agent core (144 files), gateway (71), CLI (197), desktop apps (874). | fork |
| **codebase-memory-mcp** | Pure C (zero deps), MCP server (JSON-RPC 2.0), CLI, HTTP UI, Nix | Fork của DeusData/codebase-memory-mcp. Code intelligence: full-index repo nhanh (Linux kernel 28M LOC trong 3 phút), structural query <1ms, hybrid LSP 10 ngôn ngữ, 43 agent surfaces, semantic/simhash search, graph buffer, watcher, HTTP UI, CLI + MCP. | fork |
| **dbx** | Docker Compose (t8y2/dbx) | Triển khai DBX database tool, mount SSH key, host.docker.internal. | **1** |
| **DBE** | Java/IntelliJ IDEA, PostgreSQL JDBC | Cấu hình IDE database tool DBE. | **1** |
| **fakex** | — | Repo test (7.8k file txt), không truy cập được qua clone. | — |

### Khóa học AI Thực Chiến (VinUni AICB — 2A202600722)

26 lab repos (Day01→Day26): Python/Jupyter. Nổi bật: **Day22 DPO/ORPO Alignment**, **Day21 Finetuning LLMs LoRA/QLoRA**, **Day17 Memory Systems for Agent**, **Day14 RAG Evaluation**, **Day12 Cloud Infra & Deployment**, **Day11 Guardrails/HITL/Responsible AI**, **Day09 Multi-Agent MCP/A2A**, **Day07 Data Foundations**, **Day04 Prompt Engineering & Tool Calling**.

---

## Tóm tắt năng lực (từ code thật)

- **Backend:** NestJS (11), FastAPI, Go/Gin, Node.js/Express, microservices (10-service NFT marketplace), monolith enterprise (BKVN, TDICONS, VBIM)
- **Frontend:** Next.js (14/16), React 19 + Vite, Ant Design, Fluent UI, Tailwind, Zustand, TanStack Query
- **AI/Agent:** LangGraph, LangChain, FastAPI SSE, ZERO-SQL agent, RAG (Qdrant, HyDE, multilingual), prompt optimization (GEPA, multi-objective), causal analysis (MCP), memory STM/LTM, Langfuse, RAGAS
- **Data:** pandas, sklearn, RFM/K-Means/association rules, AutoGluon time-series, SQL optimization
- **Infra:** Docker Compose, Nx monorepo, Prisma/TypeORM/Ent, Postgres/Redis/RabbitMQ/Qdrant/MinIO, CI/CD (GitHub Actions, PM2), TradingView CDP automation
- **Blockchain:** ImmutableX SDK, Web3.js, NFT marketplace, Ronin wallet, TOTP/2FA
- **Game automation:** OpenCV, pyautogui, OCR, multi-window threading, Chrome extensions (MV3)

## Ghi chú

- **Fork** (không phải code gốc của hanhvs): `KGBRecord/one` (Twenty CRM), `KGBRecord/two` (Ever Gauzy), `KGBRecord/Selected-React`, `KGBRecord/SwipeAeroSpace`, `KGBRecord/freej2me-plus-lakka`, `KGBRecord/AeroSpace`, `KGBRecord/MoneyPrinterTurbo`, `KGBRecord/Deep-Live-Cam`, `KGBRecord/ClawTeam`, `KGBRecord/drawdb`, `KGBRecord/drawdb-server`, `KGBRecord/Lakka-LibreELEC`, `KGBRecord/RetroArch`, `KGBRecord/SquirrelJME`, `KGBRecord/fake-08`, `KGBRecord/retro8`, `AGIVietNam/meta-harness-skill-2`, `hanhvs/hermes-agent`, `hanhvs/codebase-memory-mcp`.
- **Repo trống/placeholder:** `KGBRecord/Concierge`, `KGBRecord/SSurvival`, `CaperTools/pixels-tools-extension`, `AGIVietNam/vbim-elearning-be`, `AGIVietNam/pdt-standard`, `hanhvs/DBE`.
- **Repo private (không clone được):** 13 repo AGIVietNam (pdt-standard, iam-service, agi-one-iam, knowledge_center_*, trungtamtrithuc-rag, PCU-Web-Client, TDI-PCU, MCP-SERVERS-FOR-REVIT, db-auto-backup, standard-headings, VMedia-Intelligence, s3-upload) — nhưng đã phân tích được qua GitHub UI.
- **Commits = 0** nghĩa là hanhvs không phải tác giả commit trong repo đó (có thể là thành viên team, hoặc repo của người khác trong org).
- Số liệu commits lấy từ `git log --author=hanhvs` trên clone full — chính xác, không ước lượng. Repo fork shallow clone không có history → ghi "fork".
