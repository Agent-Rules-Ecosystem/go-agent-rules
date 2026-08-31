# Testing, Mocks y Benchmarks en Go

---

## 🧪 Table-Driven Tests (Patrón Estándar)

```go
func TestCalculate(t *testing.T) {
    tests := []struct {
        name     string
        input    int
        expected int
        wantErr  bool
    }{
        {"valid input", 5, 10, false},
        {"zero input", 0, 0, false},
    }

    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            got, err := Calculate(tt.input)
            if (err != nil) != tt.wantErr {
                t.Errorf("Calculate() error = %v, wantErr %v", err, tt.wantErr)
                return
            }
            if got != tt.expected {
                t.Errorf("Calculate() = %v, want %v", got, tt.expected)
            }
        })
    }
}
```

---

## ⚡ Comandos de Verificación

- `go test ./...`: Ejecutar suite completa de pruebas.
- `go test -v -cover ./...`: Cobertura de pruebas.
- `go test -bench=. ./...`: Ejecutar benchmarks.
- `golangci-lint run`: Verificación estática y linters.
