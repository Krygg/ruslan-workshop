FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /app
COPY ./Temp/*.csproj ./
RUN dotnet restore Temp.csproj
COPY ./Temp/. ./
RUN dotnet publish Temp.csproj -c Release -o pub

FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS runtime
WORKDIR /app
COPY --from=0 /app/pub .
ENTRYPOINT ["dotnet", "Temp.dll"]