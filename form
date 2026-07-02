/*
  form3.js
  Author: Mohammed Lawal
  Date: 06/16/2026
  Description: External JS for Opal Medical HW3 - live field-by-field validation.
               All checks run onblur/oninput. Submit button only appears when no errors.
*/

/* ── ERROR COUNTER ──────────────────────────────────────────────── */
let errorCount = 0;

function setError(fieldId, message) {
  const span = document.getElementById(fieldId + "-err");
  if (span) {
    span.textContent = message;
    span.style.color = "red";
  }
}

function clearError(fieldId) {
  const span = document.getElementById(fieldId + "-err");
  if (span) span.textContent = "";
}

function updateSubmitButton() {
  // Count all visible error spans
  const errors = document.querySelectorAll(".err-msg");
  let hasErrors = false;
  errors.forEach(e => { if (e.textContent.trim() !== "") hasErrors = true; });
  document.getElementById("btn-submit").style.display = hasErrors ? "none" : "inline-block";
}

/* ── FIRST NAME ─────────────────────────────────────────────────── */
function validateFname() {
  const val = document.getElementById("fname").value.trim();
  if (val === "") {
    setError("fname", "⚠ First name is required.");
  } else if (!/^[A-Za-z'\-]{1,30}$/.test(val)) {
    setError("fname", "⚠ Letters, apostrophes, and dashes only (1–30 chars).");
  } else {
    clearError("fname");
  }
  updateSubmitButton();
}

/* ── MIDDLE INITIAL ─────────────────────────────────────────────── */
function validateMI() {
  const val = document.getElementById("mi").value.trim();
  if (val === "") { clearError("mi"); updateSubmitButton(); return; }
  if (!/^[A-Za-z]$/.test(val)) {
    setError("mi", "⚠ One letter only.");
  } else {
    clearError("mi");
  }
  updateSubmitButton();
}

/* ── LAST NAME ──────────────────────────────────────────────────── */
function validateLname() {
  const val = document.getElementById("lname").value.trim();
  if (val === "") {
    setError("lname", "⚠ Last name is required.");
  } else if (!/^[A-Za-z'\-]{1,30}$/.test(val)) {
    setError("lname", "⚠ Letters, apostrophes, and dashes only (1–30 chars).");
  } else {
    clearError("lname");
  }
  updateSubmitButton();
}

/* ── DATE OF BIRTH ──────────────────────────────────────────────── */
function validateDOB() {
  const val = document.getElementById("dob").value;
  if (!val) {
    setError("dob", "⚠ Date of birth is required.");
    updateSubmitButton(); return;
  }
  const dob = new Date(val);
  const today = new Date();
  const minDate = new Date();
  minDate.setFullYear(today.getFullYear() - 120);

  if (dob > today) {
    setError("dob", "⚠ Date of birth cannot be in the future.");
  } else if (dob < minDate) {
    setError("dob", "⚠ Date of birth cannot be more than 120 years ago.");
  } else {
    clearError("dob");
  }
  updateSubmitButton();
}

/* ── SSN: auto-format as you type ───────────────────────────────── */
function formatSSN() {
  const field = document.getElementById("ssn");
  let val = field.value.replace(/\D/g, ""); // digits only
  if (val.length > 9) val = val.substring(0, 9);
  if (val.length > 5) {
    val = val.substring(0, 3) + "-" + val.substring(3, 5) + "-" + val.substring(5);
  } else if (val.length > 3) {
    val = val.substring(0, 3) + "-" + val.substring(3);
  }
  field.value = val;
  validateSSN();
}

function validateSSN() {
  const val = document.getElementById("ssn").value.trim();
  if (val === "") { clearError("ssn"); updateSubmitButton(); return; }
  if (!/^\d{3}-\d{2}-\d{4}$/.test(val)) {
    setError("ssn", "⚠ Must be in format XXX-XX-XXXX (digits only).");
  } else {
    clearError("ssn");
  }
  updateSubmitButton();
}

/* ── PHONE ──────────────────────────────────────────────────────── */
function validatePhone() {
  const val = document.getElementById("phone").value.trim();
  if (val === "") { clearError("phone"); updateSubmitButton(); return; }
  if (!/^\d{3}-\d{3}-\d{4}$/.test(val)) {
    setError("phone", "⚠ Format must be 000-000-0000.");
  } else {
    clearError("phone");
  }
  updateSubmitButton();
}

/* ── EMAIL ──────────────────────────────────────────────────────── */
function validateEmail() {
  const field = document.getElementById("email");
  field.value = field.value.toLowerCase(); // force lowercase
  const val = field.value.trim();
  if (val === "") {
    setError("email", "⚠ Email is required.");
  } else if (!/^[a-z0-9._%+\-]+@[a-z0-9.\-]+\.[a-z]{2,}$/.test(val)) {
    setError("email", "⚠ Must be in format name@domain.tld.");
  } else {
    clearError("email");
  }
  updateSubmitButton();
}

/* ── ADDRESS LINE 1 ─────────────────────────────────────────────── */
function validateAddr1() {
  const val = document.getElementById("addr1").value.trim();
  if (val.length < 2 || val.length > 30) {
    setError("addr1", "⚠ Required. Must be 2–30 characters.");
  } else {
    clearError("addr1");
  }
  updateSubmitButton();
}

/* ── ADDRESS LINE 2 ─────────────────────────────────────────────── */
function validateAddr2() {
  const val = document.getElementById("addr2").value.trim();
  if (val === "") { clearError("addr2"); updateSubmitButton(); return; }
  if (val.length < 2 || val.length > 30) {
    setError("addr2", "⚠ If entered, must be 2–30 characters.");
  } else {
    clearError("addr2");
  }
  updateSubmitButton();
}

/* ── CITY ───────────────────────────────────────────────────────── */
function validateCity() {
  const val = document.getElementById("city").value.trim();
  if (val.length < 2 || val.length > 30) {
    setError("city", "⚠ Required. Must be 2–30 characters.");
  } else {
    clearError("city");
  }
  updateSubmitButton();
}

/* ── STATE ──────────────────────────────────────────────────────── */
function validateState() {
  const val = document.getElementById("state").value;
  if (!val) {
    setError("state", "⚠ Please select a state.");
  } else {
    clearError("state");
  }
  updateSubmitButton();
}

/* ── ZIP ────────────────────────────────────────────────────────── */
function validateZip() {
  const field = document.getElementById("zip");
  let val = field.value.trim();
  // Truncate to 5 digits
  const digits = val.replace(/\D/g, "").substring(0, 5);
  field.value = digits;
  if (!/^\d{5}$/.test(digits)) {
    setError("zip", "⚠ Zip code must be exactly 5 digits.");
  } else {
    clearError("zip");
  }
  updateSubmitButton();
}

/* ── USER ID ────────────────────────────────────────────────────── */
function validateUserID() {
  const field = document.getElementById("userid");
  field.value = field.value.toLowerCase();
  const val = field.value.trim();
  if (val === "") {
    setError("userid", "⚠ User ID is required.");
  } else if (/^[0-9]/.test(val)) {
    setError("userid", "⚠ User ID cannot start with a number.");
  } else if (val.length < 5 || val.length > 20) {
    setError("userid", "⚠ Must be 5–20 characters.");
  } else if (/[^a-z0-9_\-]/.test(val)) {
    setError("userid", "⚠ Only letters, numbers, dashes, and underscores allowed. No spaces.");
  } else {
    clearError("userid");
  }
  updateSubmitButton();
}

/* ── PASSWORD ───────────────────────────────────────────────────── */
function validatePassword() {
  const pwd = document.getElementById("password").value;
  const uid = document.getElementById("userid").value.toLowerCase();
  const fname = document.getElementById("fname").value.toLowerCase();
  const lname = document.getElementById("lname").value.toLowerCase();
  let errors = [];

  if (pwd.length < 8 || pwd.length > 30) errors.push("8–30 characters required");
  if (!/[A-Z]/.test(pwd)) errors.push("at least 1 uppercase letter");
  if (!/[a-z]/.test(pwd)) errors.push("at least 1 lowercase letter");
  if (!/[0-9]/.test(pwd)) errors.push("at least 1 number");
  if (!/[!@#%^&*()\-_+=\\\/><.,`~]/.test(pwd)) errors.push("at least 1 special character");
  if (/"/.test(pwd)) errors.push('no double quotes allowed');
  if (uid && pwd.toLowerCase().includes(uid)) errors.push("cannot contain your User ID");
  if (fname && pwd.toLowerCase().includes(fname)) errors.push("cannot contain your first name");
  if (lname && pwd.toLowerCase().includes(lname)) errors.push("cannot contain your last name");

  if (errors.length > 0) {
    setError("password", "⚠ Password needs: " + errors.join(", ") + ".");
  } else {
    clearError("password");
  }
  validateConfirmPwd();
  updateSubmitButton();
}

/* ── CONFIRM PASSWORD ───────────────────────────────────────────── */
function validateConfirmPwd() {
  const pwd = document.getElementById("password").value;
  const confirm = document.getElementById("confirm-pwd").value;
  if (confirm === "") {
    setError("confirm-pwd", "⚠ Please re-enter your password.");
  } else if (pwd !== confirm) {
    setError("confirm-pwd", "⚠ Passwords do not match.");
  } else {
    clearError("confirm-pwd");
  }
  updateSubmitButton();
}

/* ── SLIDER ─────────────────────────────────────────────────────── */
function updateSlider(val) {
  document.getElementById("health-val").innerText = val;
}

/* ── DATE LIMITS ────────────────────────────────────────────────── */
function setupDateLimits() {
  const today = new Date();
  const maxDOB = today.toISOString().split("T")[0];
  const minDOBDate = new Date();
  minDOBDate.setFullYear(today.getFullYear() - 120);
  const minDOB = minDOBDate.toISOString().split("T")[0];
  const dobField = document.getElementById("dob");
  if (dobField) {
    dobField.setAttribute("max", maxDOB);
    dobField.setAttribute("min", minDOB);
  }
}

/* ── VALIDATE ALL (VALIDATE BUTTON) ─────────────────────────────── */
function validateAll() {
  validateFname();
  validateMI();
  validateLname();
  validateDOB();
  validateSSN();
  validatePhone();
  validateEmail();
  validateAddr1();
  validateAddr2();
  validateCity();
  validateState();
  validateZip();
  validateUserID();
  validatePassword();
  validateConfirmPwd();
  updateSubmitButton();

  const btn = document.getElementById("btn-submit");
  if (btn.style.display === "none" || btn.style.display === "") {
    alert("⚠ Please fix all errors before submitting.");
  } else {
    btn.scrollIntoView({ behavior: "smooth" });
  }
}

/* ── REVIEW PANEL ───────────────────────────────────────────────── */
function showReview() {
  validateAll();

  const fname  = document.getElementById("fname").value || "—";
  const mi     = document.getElementById("mi").value || "";
  const lname  = document.getElementById("lname").value || "—";
  const dob    = document.getElementById("dob").value || "—";
  const ssn    = document.getElementById("ssn").value ? "***-**-" + document.getElementById("ssn").value.slice(-4) : "—";
  const phone  = document.getElementById("phone").value || "—";
  const email  = document.getElementById("email").value || "—";
  const addr1  = document.getElementById("addr1").value || "—";
  const addr2  = document.getElementById("addr2").value || "";
  const city   = document.getElementById("city").value || "—";
  const stateEl = document.getElementById("state");
  const state  = stateEl.options[stateEl.selectedIndex]?.text || "—";
  const zip    = document.getElementById("zip").value || "—";
  const gender = document.querySelector('input[name="gender"]:checked')?.value || "—";
  const vaccinated = document.querySelector('input[name="vaccinated"]:checked')?.value || "—";
  const insurance = document.querySelector('input[name="insurance"]:checked')?.value || "—";
  const conditions = [...document.querySelectorAll('input[name="conditions"]:checked')]
    .map(c => c.value).join(", ") || "None";
  const health = document.getElementById("health").value;
  const symptoms = document.getElementById("symptoms").value || "None provided";
  const userid = document.getElementById("userid").value || "—";

  const html = `
    <h3>📋 Please Review Your Information</h3>
    <table class="review-table">
      <tr><th colspan="2">Personal Information</th></tr>
      <tr><td>Full Name</td><td>${fname} ${mi ? mi + "." : ""} ${lname}</td></tr>
      <tr><td>Date of Birth</td><td>${dob}</td></tr>
      <tr><td>SSN (masked)</td><td>${ssn}</td></tr>
      <tr><th colspan="2">Contact</th></tr>
      <tr><td>Phone</td><td>${phone}</td></tr>
      <tr><td>Email</td><td>${email}</td></tr>
      <tr><th colspan="2">Address</th></tr>
      <tr><td>Address</td><td>${addr1}${addr2 ? "<br>" + addr2 : ""}<br>${city}, ${state} ${zip}</td></tr>
      <tr><th colspan="2">Demographics & Medical</th></tr>
      <tr><td>Gender</td><td>${gender}</td></tr>
      <tr><td>Vaccinated?</td><td>${vaccinated}</td></tr>
      <tr><td>Has Insurance?</td><td>${insurance}</td></tr>
      <tr><td>Conditions</td><td>${conditions}</td></tr>
      <tr><td>Health Score</td><td>${health} / 10</td></tr>
      <tr><td>Symptoms</td><td>${symptoms}</td></tr>
      <tr><th colspan="2">Account</th></tr>
      <tr><td>User ID</td><td>${userid}</td></tr>
      <tr><td>Password</td><td>••••••••</td></tr>
    </table>
    <p style="margin-top:12px; font-size:0.85em; color:#666;">
      If everything looks correct and there are no errors above, click <strong>Submit Registration</strong>.
    </p>
  `;

  const panel = document.getElementById("review-panel");
  panel.innerHTML = html;
  panel.style.display = "block";
  panel.scrollIntoView({ behavior: "smooth" });
}

/* ── INIT ───────────────────────────────────────────────────────── */
window.addEventListener("DOMContentLoaded", function () {
  setupDateLimits();

  // Hide submit button initially
  document.getElementById("btn-submit").style.display = "none";

  // Attach live listeners
  document.getElementById("fname")?.addEventListener("blur", validateFname);
  document.getElementById("mi")?.addEventListener("blur", validateMI);
  document.getElementById("lname")?.addEventListener("blur", validateLname);
  document.getElementById("dob")?.addEventListener("change", validateDOB);
  document.getElementById("ssn")?.addEventListener("input", formatSSN);
  document.getElementById("ssn")?.addEventListener("blur", validateSSN);
  document.getElementById("phone")?.addEventListener("blur", validatePhone);
  document.getElementById("email")?.addEventListener("blur", validateEmail);
  document.getElementById("addr1")?.addEventListener("blur", validateAddr1);
  document.getElementById("addr2")?.addEventListener("blur", validateAddr2);
  document.getElementById("city")?.addEventListener("blur", validateCity);
  document.getElementById("state")?.addEventListener("change", validateState);
  document.getElementById("zip")?.addEventListener("blur", validateZip);
  document.getElementById("userid")?.addEventListener("blur", validateUserID);
  document.getElementById("password")?.addEventListener("input", validatePassword);
  document.getElementById("confirm-pwd")?.addEventListener("input", validateConfirmPwd);
});
