import React, { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Select, SelectTrigger, SelectValue, SelectContent, SelectItem } from "@/components/ui/select";
import { Table, TableHeader, TableRow, TableHead, TableBody, TableCell } from "@/components/ui/table";

export default function CareerSystem() {
  const [professionals, setProfessionals] = useState([
    { name: "Maria Silva", role: "Enfermeira", status: "Ativo" },
    { name: "João Oliveira", role: "Médico", status: "Inativo" },
  ]);

  const [filters, setFilters] = useState({ search: "", role: "", status: "" });
  const [newProfessional, setNewProfessional] = useState({ name: "", role: "" });

  const handleFilterChange = (field, value) => {
    setFilters({ ...filters, [field]: value });
  };

  const handleAddProfessional = () => {
    if (newProfessional.name && newProfessional.role) {
      setProfessionals([...professionals, { ...newProfessional, status: "Ativo" }]);
      setNewProfessional({ name: "", role: "" });
    }
  };

  const filteredProfessionals = professionals.filter((prof) => {
    const matchesSearch = prof.name.toLowerCase().includes(filters.search.toLowerCase());
    const matchesRole = filters.role ? prof.role === filters.role : true;
    const matchesStatus = filters.status ? prof.status === filters.status : true;
    return matchesSearch && matchesRole && matchesStatus;
  });

  return (
    <div className="p-6 space-y-6">
      <h1 className="text-2xl font-bold">Sistema de Gestão de Cargos e Carreira - Saúde Pública</h1>

      {/* Section: Search and Filters */}
      <Card className="p-4">
        <CardContent className="space-y-4">
          <h2 className="text-xl font-semibold">Filtros</h2>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
            <Input
              placeholder="Buscar por nome ou cargo"
              value={filters.search}
              onChange={(e) => handleFilterChange("search", e.target.value)}
            />
            <Select onValueChange={(value) => handleFilterChange("role", value)}>
              <SelectTrigger>
                <SelectValue placeholder="Selecione um cargo" />
              </SelectTrigger>
              <SelectContent>
                <SelectItem value="">Todos</SelectItem>
                <SelectItem value="Enfermeira">Enfermeira</SelectItem>
                <SelectItem value="Médico">Médico</SelectItem>
                <SelectItem value="Técnico de Enfermagem">Técnico de Enfermagem</SelectItem>
              </SelectContent>
            </Select>
            <Select onValueChange={(value) => handleFilterChange("status", value)}>
              <SelectTrigger>
                <SelectValue placeholder="Filtrar por status" />
              </SelectTrigger>
              <SelectContent>
                <SelectItem value="">Todos</SelectItem>
                <SelectItem value="Ativo">Ativo</SelectItem>
                <SelectItem value="Inativo">Inativo</SelectItem>
              </SelectContent>
            </Select>
          </div>
          <Button className="mt-4">Aplicar Filtros</Button>
        </CardContent>
      </Card>

      {/* Section: Career Table */}
      <Card className="p-4">
        <CardContent>
          <h2 className="text-xl font-semibold mb-4">Lista de Profissionais</h2>
          <Table>
            <TableHeader>
              <TableRow>
                <TableHead>Nome</TableHead>
                <TableHead>Cargo</TableHead>
                <TableHead>Status</TableHead>
                <TableHead>Ações</TableHead>
              </TableRow>
            </TableHeader>
            <TableBody>
              {filteredProfessionals.map((prof, index) => (
                <TableRow key={index}>
                  <TableCell>{prof.name}</TableCell>
                  <TableCell>{prof.role}</TableCell>
                  <TableCell>{prof.status}</TableCell>
                  <TableCell>
                    <Button variant="outline">Visualizar</Button>
                  </TableCell>
                </TableRow>
              ))}
            </TableBody>
          </Table>
        </CardContent>
      </Card>

      {/* Section: Add New Professional */}
      <Card className="p-4">
        <CardContent className="space-y-4">
          <h2 className="text-xl font-semibold">Adicionar Novo Profissional</h2>
          <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
            <Input
              placeholder="Nome do Profissional"
              value={newProfessional.name}
              onChange={(e) => setNewProfessional({ ...newProfessional, name: e.target.value })}
            />
            <Select onValueChange={(value) => setNewProfessional({ ...newProfessional, role: value })}>
              <SelectTrigger>
                <SelectValue placeholder="Selecione o Cargo" />
              </SelectTrigger>
              <SelectContent>
                <SelectItem value="Enfermeira">Enfermeira</SelectItem>
                <SelectItem value="Médico">Médico</SelectItem>
                <SelectItem value="Técnico de Enfermagem">Técnico de Enfermagem</SelectItem>
              </SelectContent>
            </Select>
          </div>
          <Button className="mt-4" onClick={handleAddProfessional}>Salvar</Button>
        </CardContent>
      </Card>
    </div>
  );
}
npm install
npm start

