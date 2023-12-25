<template>
  <div class="container py-5">
    <div class="d-flex flex-left">
      <div class="mb-4 text-secondary">
        <h1>All Dashboard Hosts</h1>
      </div>
      <div class="dropdown m-2">
        <button class="btn btn-secondary dropdown-toggle text-secondary" style="background-color: white;" type="button" id="dropdownMenuButton" data-toggle="dropdown"
          aria-haspopup="true" aria-expanded="false">
          Ecommerce
        </button>
      </div>
    </div>
    <div class="table-responsive">
      <table class="table table-hover align-middle">
        <thead>
          <tr>
            <th scope="col">Hostname</th>
            <th scope="col">Name servers</th>
            <th scope="col">DNSSEC</th>
            <th scope="col">TLS</th>
            <th scope="col">DANE</th>
            <th scope="col">SPF</th>
            <th scope="col">DMARC</th>
            <th scope="col">TLS</th>
            <th scope="col">Cookies</th>
            <th scope="col">Mixed content</th>
            <th scope="col">HSTS</th>
            <th scope="col">CSP</th>
            <th scope="col">Security headers</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="host in hosts" :key="host.hostname">
            <td>
              <NuxtLink :to="`/details/${host.hostname}`">
                {{ host.hostname }}
              </NuxtLink>
            </td>
            <td><i class="bi bi-check-lg text-success"></i></td>
            <td>{{ host.dnssec }}</td>
            <td><i class="bi bi-check-lg text-success"></i></td>
            <td>{{ host.dane }}</td>
            <td><i class="bi bi-check-lg text-success"></i></td>
            <td><i :class="getStatusClass(host.dmarc)"></i></td>
            <td><i class="bi bi-check-lg text-success"></i></td>
            <td><i class="bi bi-check-lg text-success"></i></td>
            <td><i :class="getStatusClass(host.mixedContent)"></i></td>
            <td><i class="bi bi-check-lg text-success"></i></td>
            <td><i class="bi bi-check-lg text-success"></i></td>
            <td><i class="bi bi-check-lg text-success"></i></td>
          </tr>
        </tbody>
      </table>
    </div>
    <!-- Pagination (static for this example) -->
    <nav aria-label="Page navigation">
      <ul class="pagination justify-content-center">
        <li class="page-item disabled">
          <a class="page-link">Previous</a>
        </li>
        <li class="page-item active"><a class="page-link" href="#">1</a></li>
        <li class="page-item"><a class="page-link" href="#">2</a></li>
        <li class="page-item"><a class="page-link" href="#">3</a></li>
        <li class="page-item">
          <a class="page-link" href="#">Next</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const hosts = ref([
  { hostname: 'aboutyou.ch', dnssec: '-', dane: '-', dmarc: 'ok', mixedContent: 'warning' },
  { hostname: 'ackermann.ch', dnssec: 'ok', dane: '-', dmarc: 'error', mixedContent: 'ok' },
  { hostname: 'adidas.ch', dnssec: '-', dane: '-', dmarc: 'ok', mixedContent: 'ok' },
  { hostname: 'adspot.ch', dnssec: 'ok', dane: '-', dmarc: 'ok', mixedContent: 'error' },
  { hostname: 'airbnb.ch', dnssec: 'ok', dane: '-', dmarc: 'ok', mixedContent: 'error' },
  { hostname: 'allposters.ch', dnssec: 'ok', dane: '-', dmarc: 'ok', mixedContent: 'error' },
  { hostname: 'anibis.ch', dnssec: 'ok', dane: '-', dmarc: 'ok', mixedContent: 'error' },
  { hostname: 'auto-online.ch', dnssec: 'ok', dane: '-', dmarc: 'ok', mixedContent: 'error' },
  { hostname: 'autoscout24.ch', dnssec: 'ok', dane: '-', dmarc: 'ok', mixedContent: 'error' },
  { hostname: 'bauundhobby.ch', dnssec: 'ok', dane: '-', dmarc: 'ok', mixedContent: 'error' },
  { hostname: 'bettybossi.ch', dnssec: 'ok', dane: '-', dmarc: 'ok', mixedContent: 'error' },
]);

function getStatusClass(status) {
  if (status === 'ok') {
    return 'bi bi-check-lg text-success';
  } else if (status === 'warning') {
    return 'bi bi-exclamation-triangle-fill text-warning';
  } else if (status === 'error') {
    return 'bi bi-x-lg text-danger';
  } else {
    return '';
  }
}
</script>

<style scoped>
</style>