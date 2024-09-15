#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

# base image creation (will be used in final)
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
USER app
WORKDIR /app
EXPOSE 8080
EXPOSE 8081

# build stage
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
ARG BUILD_CONFIGURATION=Release
WORKDIR /src
COPY ["FlowPlannerAPI/FlowPlannerAPI.csproj", "FlowPlannerAPI/"]
RUN dotnet restore "./FlowPlannerAPI/FlowPlannerAPI.csproj"
COPY . .
WORKDIR "/src/FlowPlannerAPI"
RUN dotnet build "./FlowPlannerAPI.csproj" -c $BUILD_CONFIGURATION -o /app/build

# publish stage
FROM build AS publish
ARG BUILD_CONFIGURATION=Release
RUN dotnet publish "./FlowPlannerAPI.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false

# final stage - copying published folder to final image
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "FlowPlannerAPI.dll"]