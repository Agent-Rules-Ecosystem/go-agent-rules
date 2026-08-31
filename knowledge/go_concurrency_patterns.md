# Patrones de Concurrencia y Canales en Go

> Guía técnica de concurrencia segura con Goroutines, Channels y `context.Context`.

---

## ⚡ Reglas de Oro en Concurrencia Go

1. **Nunca inicies una Goroutine sin saber cómo finalizarla**: Evita memory leaks de goroutines huérfanas.
2. **Propaga siempre `context.Context`**: Pasa `ctx` como primer argumento en funciones de I/O o red (`ctx context.Context`).
3. **Usa `sync.WaitGroup` o `errgroup.Group`**: Para sincronizar la finalización de múltiples tareas concurrentes.
4. **Protección de Estado**: Usa `sync.Mutex` o `sync.RWMutex` para memoria compartida, o prefiere canales ("Do not communicate by sharing memory; instead, share memory by communicating").

---

## 🛠️ Patrón Worker Pool

```go
func Worker(id int, jobs <-chan Job, results chan<- Result, wg *sync.WaitGroup) {
    defer wg.Done()
    for job := range jobs {
        results <- process(job)
    }
}
```
