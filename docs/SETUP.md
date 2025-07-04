# Setup Guide for Herfy Backend

This guide explains how to set up and run the Herfy Backend locally.

## Prerequisites
- **.NET SDK 8.0**: Download from [here](https://dotnet.microsoft.com/download).
- **PostgreSQL**: Download from [here](https://www.postgresql.org/download/).
- **Git**: Download from [here](https://git-scm.com/downloads).
- **IDE**: Visual Studio, VS Code, or Rider.

## Installation
1. **Clone the repository**:
   ```bash
   git clone https://github.com/AOLabs/herfy-backend.git
   cd harfy-backend
   ```
2. **Install dependencies**:
   ```bash
   dotnet restore
   ```
3. **Set up PostgreSQL**:
   - Create a database named `herfy`:
     ```sql
     CREATE DATABASE harfy;
     ```
   - Update `src/HerfyBackend/appsettings.json` with your PostgreSQL credentials:
     ```json
     "ConnectionStrings": {
       "DefaultConnection": "Host=localhost;Database=herfy;Username=postgres;Password=your_password"
     }
     ```
4. **Run migrations**:
   ```bash
   cd src/HerfyBackend
   dotnet ef database update
   ```
5. **Configure JWT**:
   - Update `src/HerfyBackend/appsettings.json` with a secure JWT key:
     ```json
     "Jwt": {
       "Issuer": "HerfyBackend",
       "Audience": "HerfyClients",
       "SecretKey": "your_very_long_secret_key_32_chars"
     }
     ```
6. **Run the project**:
   ```bash
   dotnet run
   ```
7. **Access Swagger**:
   - Open `https://localhost:5001/swagger` to test the APIs.

## Troubleshooting
- **Database connection error**: Ensure PostgreSQL is running and credentials are correct.
- **JWT errors**: Verify the `Jwt.SecretKey` is at least 32 characters.

## Questions?
Reach out via GitHub Issues or email [your-email@example.com].