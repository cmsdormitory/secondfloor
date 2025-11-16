# cmos.dormitory

Dormitory Points & Rewards System — a lightweight platform designed for managing points, evaluations, and redemptions in dormitory or shared-living scenarios.

## Project Overview
cmos.dormitory turns daily dorm activities (cleaning, duty shifts, participation, infractions, etc.) into quantifiable "points" and provides a transparent, auditable process for issuing and redeeming those points. The system supports multiple roles (admin, dorm leader, member) with clear permission boundaries to make dorm self-governance and management committee operations straightforward.

## Core Features
- Points management: automatic or manual awarding and deduction of points via rules for tasks, inspections, activity check-ins, and infractions.
- Redemption: members can redeem points for goods, vouchers or services (e.g., laundry pass, equipment borrowing).
- Approval and audit: configurable approval workflows for redemptions and a complete transaction log for every points change.
- Multi-role support: Admin (configure rules, manage products, approve), Dorm Leader (submit assessments, approve small redemptions), Member (view points, request redemptions).
- Notifications: notify users of points changes and redemption status via in-app notifications, email, or SMS (optional).
- Extensible catalog and rules engine to support promotions and bulk issuances.

## Use Cases
- Campus dormitory incentive programs (cleanliness, duty roster, civilized dorm awards)
- Staff dormitories or co-living spaces that want a lightweight rewards system
- Event reward systems with physical / service exchange

## Technical Highlights (example)
- Clear frontend / backend separation for easier development and deployment
- Configurable scoring rules to reduce the need for code changes for common ops
- Audit logging and transactional safety to ensure correctness of points flows

## Quick Start — Based on this repository's current contents
Note: I inspected the repository root and found a static frontend file (index.html). There is no package.json, no backend directory, and no migration scripts in the repository root. The instructions below cover the common cases and provide executable commands for serving the current static site, plus guidance if a Node-based dev environment exists later.

1. Clone the repository
   git clone https://github.com/JasonChow123/cmos.dormitory.git
   cd cmos.dormitory

2. Inspect repository to determine project type
   ls -la
   # Check for Node.js project files
   if [ -f package.json ]; then echo "Found package.json"; else echo "No package.json found — repository appears to be a static site"; fi

3. If the repository is a static site (current state: index.html present)
   - Open the file directly in your browser:
     - Double-click index.html or open with your browser (file://...).
   - Or serve it locally with a lightweight static server:

     Python 3:
       python3 -m http.server 8000
       # then open http://localhost:8000 in your browser

     Node (if you have npm available):
       npx serve . -l 3000
       # then open http://localhost:3000

     VS Code:
       Use the Live Server extension and click "Go Live" on index.html.

4. If the repository later includes a Node.js app (package.json found)
   - Install dependencies and run:
     npm install
     npm run dev   # or npm start (use the script names defined in package.json)

   - If there are backend and frontend subdirectories:
     cd backend
     npm install
     npm run dev
     cd ../frontend
     npm install
     npm run dev

5. Database / environment configuration (only relevant if a backend is added)
   - Create a `.env` from `.env.sample` and fill values (DATABASE_URL, JWT_SECRET, etc.)
     cp .env.sample .env
     # Edit .env with real values

   - Run database creation and migrations according to the project's chosen ORM/migration tool:
     # Example (Prisma):
     npx prisma migrate dev --name init
     # Example (TypeORM):
     npm run typeorm migration:run
     # Example (Sequelize):
     npx sequelize-cli db:migrate

6. Common troubleshooting
   - If a page fails to load, open the developer console to see JS/CSS errors.
   - Ensure required static assets (images, JS bundles) are present in the repo relative to index.html.
   - If you intended a full-stack project but only see index.html, confirm whether other branches or submodules hold the backend.

Notes
- The current repository snapshot contains a static front-end file (index.html). The above Quick Start prioritizes easy ways to preview that static content.
- If you plan to add a backend or convert this into a multi-package repo, add package.json, README scripts, and a clear backend/frontend directory layout to the repository so that automated scripts (npm run dev / npm start) can be used.

## Contribution
Contributions are welcome. See CONTRIBUTING.md for details on reporting issues, creating pull requests, and coding standards.

## Contact & Support
Maintainer: @JasonChow123  
For custom features or deployment help, open an Issue or reach out via the contact listed in the repository.

## License
Add project license here (e.g., MIT, Apache-2.0).