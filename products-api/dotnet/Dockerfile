# Use the official .NET SDK image
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /app

# Copy and restore dependencies
COPY . ./
RUN dotnet restore
RUN dotnet publish -c Release -o out

# Build the final image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build /app/out .

# Expose the port and start the application
EXPOSE 8080
ENTRYPOINT ["dotnet", "api.dll"]
