FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /app
COPY ./JansKreditfond/*.csproj ./
RUN dotnet restore JansKreditfond.csproj
COPY ./JansKreditfond/. ./
RUN dotnet publish JansKreditfond.csproj -c Release -o pub

FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS runtime
WORKDIR /app
COPY --from=0 /app/pub .
ENTRYPOINT ["dotnet", "JansKreditfond.dll"]