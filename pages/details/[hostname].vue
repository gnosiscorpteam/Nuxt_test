<template>
  <div class="container py-4">
    <h1>Details for {{  hostname }}</h1>
    <div class="card mb-4">
      <div class="card-header">
        Public Report | {{ domain }}
      </div>
      <div class="card-body">
        <h5 class="card-title">{{ domain }}</h5>
        <p class="card-text">WEB SECURITY OVERVIEW</p>
        <div class="row">
          <div class="col-md-4">
            <!-- Domain Name System Section -->
            <h6>Domain Name System</h6>
            <ul class="list-unstyled">
              <li v-for="(value, name) in reportData.dns" :key="name">
                <i :class="getIconClass(value)"></i> {{ name }}
              </li>
            </ul>
            <!-- Email Section -->
            <h6>Email</h6>
            <ul class="list-unstyled">
              <li v-for="(value, name) in reportData.email" :key="name">
                <i :class="getIconClass(value)"></i> {{ name }}
              </li>
            </ul>
            <!-- WWW Section -->
            <h6>WWW</h6>
            <ul class="list-unstyled">
              <li v-for="(value, name) in reportData.www" :key="name">
                <i :class="getIconClass(value)"></i> {{ name }}
              </li>
            </ul>
          </div>
          <div class="col-md-8">
            <div class="row">
              <div class="col ">
                <h3 class="mb-3 border-bottom">WEB SECURITY OVERVIEW</h3>
                <div class="bg-light p-3 mb-3">
                  <p><strong>HTTPS</strong>: Web sites need to use encryption to help their visitors know they're in the right place, as well as provide confidentiality and content integrity...</p>
                  <p><strong>HTTPS Redirection</strong>: To deploy HTTPS properly, web sites must redirect all unsafe (plaintext) traffic to the encrypted variant. This approach ensures that no sensitive data is exposed and that further security technologies can be activated.</p>
                  <p><strong>HTTP Strict Transport Security (HSTS)</strong>: HSTS is an HTTP extension that instructs browsers to remember sites that use encryption and enforce strict security requirements. Without HSTS, active network attacks are easy to carry out.</p>
                  <p><strong>HSTS Preloading</strong>: HSTS Preloading is informing browsers in advance about a site's use of HSTS, which means that strict security can be enforced on the first visit. This approach provides best HTTPS security available today.</p>
                  <p><strong>Content Security Policy (CSP)</strong>: CSP is an additional security layer that enables web sites to control browser behavior, creating a safety net that can counter attacks such as cross-site scripting.</p>
                </div>
                <h3 class="mb-3 border-bottom">EMAIL SECURITY OVERVIEW</h3>
                <div class="bg-light p-3 mb-3">
                  <p><strong>STARTTLS</strong>: All hosts that receive email need encryption to ensure confidentiality of email messages. Email servers thus need to support STARTTLS, as well as provide decent TLS configuration and correct certificates.</p>
                  <p><strong>SPF</strong>: Sender Policy Framework (SPF) enables organizations to designate servers that are allowed to send email messages on their behalf. With SPF in place, spam is easier to identify.</p>
                  <p><strong>DMARC</strong>: Domain-based Message Authentication, Reporting, and Conformance (DMARC) is a mechanism that allows organizations to specify how unauthenticated email (identified using SPF and DKIM) should be handled. There are issues with this site's DMARC configuration.</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();
const hostname = route.params.hostname;
const domain = ref(hostname);

const reportData = ref({
  dns: {
    'DNS Zone': true,
    'DNS Records': true,
    'DNSSEC': false,
    'CAA': false
  },
  email: {
    'Mail servers': true,
    'TLS': true,
    'Certificates': true,
    'MTA-STS': false,
    'TLS-RPT': false,
    'DANE': false
  },
  www: {
    'Protocols': true,
    'HTTPS (443)': true,
    'TLS': true,
    'Cookies': false,
    'Mixed Content': false
  }
});

function getIconClass(value) {
  return value
    ? 'bi bi-check-circle-fill text-success'
    : 'bi bi-x-circle-fill text-danger';
}
</script>

<style scoped>
.web-security-overview h3 {
  color: #333;
  margin-bottom: 1rem;
}

.web-security-overview div {
  display: flex;
  align-items: center;
}

.web-security-overview i {
  font-size: 1.5rem;
  margin-right: 0.5rem;
}

.web-security-overview p {
  flex-grow: 1;
  margin-bottom: 0;
}

.web-security-overview span.badge {
  margin-left: 1rem;
  font-size: 0.8rem;
  padding: 0.25em 0.6em;
  font-weight: normal;
}
</style>
