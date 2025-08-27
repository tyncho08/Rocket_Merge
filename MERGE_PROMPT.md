REMEMBER TO USE THE OPUS MODEL FOR PLANNING AND SONNET 4 FOR EXECUTION!

## Complete App Merge: RocketFind + RocketAdmin → Unified LendPro Platform

I need you to merge two independent applications (App1-RocketFind and App2-RocketAdmin) into a single unified LendPro Mortgage Platform. Execute this merge completely and autonomously with the precise specifications below.

### Context
- **App1-RocketFind**: Consumer-facing mortgage and property search application (currently ports 4200/5000)
- **App2-RocketAdmin**: Administrative loan management system (currently ports 4201/5001)
- **Target**: Single unified application on ports **4001 (frontend)** and **5001 (backend)**
- **Shared Infrastructure**: Both apps use identical database schema, authentication system, and visual design

### Critical Navigation Requirements

#### Header Navigation (Simplified)
**Always Visible:**
- Home Search
- Mortgage Tools

**Role-Based Header Links:**
- **Regular Users**: Dashboard
- **Admin Users**: Admin Dashboard + User Dashboard (admin sees both)
- **All Users**: Login/Logout

#### Home Page Hub (Dynamic Feature Cards)
**Always Visible Cards:**
- Home Search → `/search`
- Mortgage Tools → `/mortgage-tools` 
- Market Trends → `/market-trends`

**Authenticated Regular Users Only:**
- Loan Application → `/loan-application`

**Admin Users Only:**
- Loan Management → `/admin/loans`
- User Management → `/admin/users`

#### Functionality to Remove Completely
- **Property Comparison**: Delete all components, routes, and references

### Technical Specifications

#### Directory Structure
```
MergedApp-LendPro/
├── backend/                    # .NET Core 3.1 API (port 5001)
├── frontend/                   # Angular 19.2 (port 4001)  
├── database/                   # PostgreSQL initialization
├── start.sh                    # Unified startup script
├── stop.sh                     # Clean shutdown script
└── README.md                   # Complete documentation
```

#### Backend Merge Requirements
1. **Merge all controllers** from both applications
2. **Add missing admin endpoints** to LoansController:
   - `GET /api/loans` (with pagination: page, limit, status, search)
   - `PUT /api/loans/{id}/status` (admin role required)
3. **Fix CORS configuration**: Change from `http://localhost:4200` to `http://localhost:4001`
4. **Update launch settings**: Backend port 5001
5. **Preserve authentication**: JWT with role-based authorization (`[Authorize(Roles = "Admin")]`)

#### Frontend Merge Requirements
1. **Merge all components** from both applications into single frontend
2. **Update routing**: Include all routes from both apps with proper guards
3. **Remove Property Comparison**: Delete `/comparison` route and all related components
4. **Update navigation**: Implement exact header and Home component specifications above
5. **Make Home component dynamic**: Inject AuthService and show role-based feature cards
6. **Update configuration**:
   - Package name: `"lendpro-platform"`
   - Frontend port: 4001
   - API URL: `http://localhost:5001/api`
   - App name: "LendPro - Complete Mortgage Platform"

#### Authentication & Database
- **Use existing shared database**: PostgreSQL with existing schema and test users
- **Test Accounts**:
  - Regular User: `john.doe@email.com` / `user123`
  - Admin User: `admin@mortgageplatform.com` / `admin123`
- **Authentication Flow**: JWT tokens with BCrypt password hashing
- **Role-based access**: AuthGuard for users, AdminGuard for admin features

### Startup Requirements
Create comprehensive `start.sh` script with:
- Port cleanup (kill processes on 4001/5001)
- Dependency verification (Node.js, .NET, pnpm)
- Automatic pnpm installation if missing
- Backend and frontend startup with health checks
- Detailed logging to separate log files
- User-friendly status reporting
- Error handling and timeout management

### Success Criteria Validation
The merge is successful when:
- ✅ Single application serves both consumer and admin functionality
- ✅ Navigation matches exact specifications (clean header + Home hub)
- ✅ Admin users can see both Admin Dashboard and User Dashboard in header
- ✅ All role-based feature cards work correctly in Home component
- ✅ Property Comparison functionality is completely removed
- ✅ All consumer features work (property search, mortgage tools, user dashboard)
- ✅ All admin features work (loan management, user management via Home)
- ✅ Authentication works for both test accounts with proper role-based access
- ✅ Application runs smoothly on ports 4001/5001
- ✅ Market Trends, Loan Application, Loan Management, User Management accessed via Home only

### Implementation Notes
- **CORS Fix**: Critical - update Startup.cs from port 4200 to 4001
- **Admin API**: Ensure LoansController has pagination endpoints for admin interface
- **CSS Grid**: Use responsive grid for Home feature cards to accommodate dynamic content
- **Error Handling**: Include comprehensive error handling in startup scripts
- **Documentation**: Update README with merged application structure and test accounts

Execute this merge completely and autonomously, ensuring all specifications are met precisely as outlined above.