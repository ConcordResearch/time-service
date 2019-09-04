FROM microsoft/dotnet:2.2-sdk AS build-env
WORKDIR /app
COPY . .

WORKDIR /app/TimeService
RUN ["dotnet", "restore"]
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.2-sdk
WORKDIR /app
COPY --from=build-env /app/TimeService/out/ .
EXPOSE 5050 80 443
ENTRYPOINT ["dotnet", "TimeServce.dll"]

