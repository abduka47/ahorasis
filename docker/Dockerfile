FROM registry.access.redhat.com/ubi8/dotnet-60:6.0-32.20230511125009 as builder
WORKDIR /opt/app-root/src
COPY --chown=1001 . .
RUN dotnet publish -c Release -o /opt/app-root/publish

FROM registry.access.redhat.com/ubi8/dotnet-60:6.0-32.20230511125009
EXPOSE 8081
ENV ASPNETCORE_URLS=http://*:8081
COPY --from=builder /opt/app-root/publish /opt/app-root/app
WORKDIR /opt/app-root/app
CMD ["dotnet", "ahorasis.dll"]
