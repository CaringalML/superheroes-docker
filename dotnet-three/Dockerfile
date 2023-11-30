FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
# Copy the published site directory into the container
COPY . .

ENV ASPNETCORE_URLS=http://+:5000
ENV ASPNETCORE_ENVIRONMENT=Production

EXPOSE 5000

ENTRYPOINT ["dotnet", "SuperHeroAPI.dll"]