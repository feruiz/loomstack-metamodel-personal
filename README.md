# LoomStack Meta Model

A **Strapi 5** headless CMS for defining schemas and components that LoomWire uses to draw schematics.

## 🌐 Live Demo (Strapi Cloud)

**Access the live application**: [To be updated after deployment]

- **Admin Panel**: `[strapi-cloud-url]/admin`
- **API**: `[strapi-cloud-url]/api`
- **Documentation**: `[strapi-cloud-url]/documentation`

## 🚀 Quick Start for Team Evaluation

### Option 1: Use Live Demo (Recommended)
The application is deployed on Strapi Cloud for instant access:
1. No setup required - just access the live URL above
2. Perfect for team evaluation and collaboration
3. Create admin account and start defining schemas immediately

### Option 2: Local Development
**Requirements:** Node.js >=18.0.0, Yarn package manager

```bash
# Clone the repository
git clone https://github.com/feruiz/loomstack-metamodel-personal.git
cd loomstack-metamodel-personal

# Install dependencies (Yarn required)
yarn install

# Copy environment file
cp .env.example .env

# Start development server
yarn develop
```

## 🎯 Meta Model Purpose

This system allows high-level users to define schemas for components that **LoomWire** will use through its component library to draw schematics.

**Primary Use Cases:**
- Design harness schematics with control units, connectors, pins, and wires
- Define electrical component specifications and relationships
- Create extensible schemas for any type of schematic design
- Manage component libraries for engineering teams

## 📝 First Time Setup

1. Open the admin panel URL
2. Create your first admin user
3. Start creating content types for LoomWire components:
   - **Control Units**: Electronic control modules
   - **Connectors**: Electrical connectors and pinouts
   - **Pins**: Individual pin definitions
   - **Wires**: Wire specifications
   - **Other Components**: Extensible for any schematic element

## 🛠️ Available Scripts

```bash
yarn develop     # Start with auto-reload (development)
yarn build      # Build admin panel for production
yarn start      # Start without auto-reload (production)
yarn console    # Open Strapi console
yarn deploy     # Deploy using Strapi Cloud
```

## 📚 Learn More

- [Strapi Documentation](https://docs.strapi.io) - Official Strapi documentation
- [Strapi Cloud](https://cloud.strapi.io) - Cloud hosting platform
- [Content-Type Builder](https://docs.strapi.io/user-docs/content-type-builder) - Creating content types
- [API Documentation](https://docs.strapi.io/dev-docs/api/rest) - REST API reference

---

**Ready to start?** Access the live demo above or clone this repository for local development!
