import React, { useState } from "react";
import FilterBar from "./components/FilterBar";
import KpiCards from "./components/KpiCards";
import Charts from "./components/Charts";
import DataTable from "./components/DataTable";
import projects from "./data/projects";

function App() {
  const [filters, setFilters] = useState({ year: "2025", type: "All", status: "All" });

  const filteredProjects = projects.filter((proj) => {
    return (
      (filters.type === "All" || proj.type === filters.type) &&
      (filters.status === "All" || proj.status === filters.status)
    );
  });

  return (
    <div className="p-6 bg-gray-100 min-h-screen">
      <h1 className="text-3xl font-bold mb-6">Süreç İyileştirme Dashboard</h1>
      <FilterBar filters={filters} setFilters={setFilters} />
      <KpiCards projects={filteredProjects} />
      <Charts projects={filteredProjects} />
      <DataTable projects={filteredProjects} />
    </div>
  );
}
