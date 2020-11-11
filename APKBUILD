pkgname=firmware-oneplus-msm8998
pkgver=9.0.11
pkgrel=0
pkgdesc="Firmware for OnePlus 5/5T"
url="https://github.com/JamiKettunen/firmware-mainline-oneplus5"
# Conflicts with ath10k/WCN3990/hw1.0/firmware-5.bin, qca/cr{btfw21.tlv,nv21.bin} & qcom/a530_p{fp,m4}.fw
provides="linux-firmware-ath10k linux-firmware-qca linux-firmware-qcom"
arch="aarch64"
license="proprietary"
options="!check !archcheck !strip !tracedeps pmb:cross-native"
source="$pkgname-$pkgver.zip::https://github.com/JamiKettunen/firmware-mainline-oneplus5/archive/$pkgver.zip"
_fwdir="/lib/firmware"
_ath10kdir="ath10k/WCN3990/hw1.0"
_qcomdir="qcom/OnePlus/MSM8998"

package() {
	cd "$srcdir"/firmware-mainline-oneplus5-$pkgver/

	# WLAN firmware
	for _fw in board-2.bin firmware-5.bin; do
		install -Dm644 $_ath10kdir/$_fw -t "$pkgdir"/$_fwdir/$_ath10kdir/
	done

	# Bluetooth firmware
	for _fw in crbtfw21.tlv crnv21.bin; do
		install -Dm644 qca/$_fw -t "$pkgdir"/$_fwdir/qca/
	done

	# GPU firmware
	for _fw in a530_pfp.fw a530_pm4.fw a540_gpmu.fw2 a540_zap.mbn; do
		install -Dm644 qcom/$_fw -t "$pkgdir"/$_fwdir/qcom/
	done

	# ADSP, SLPI, Modem & additional WLAN firmware
	for _fw in adsp.mbn slpi_v2.mbn mba.mbn modem.mbn modemuw.jsn wlanmdsp.mbn; do
		install -Dm644 $_qcomdir/$_fw -t "$pkgdir"/$_fwdir/$_qcomdir/
	done
}

sha512sums="85a0e290dd3c8066c11c6291c2c005f95dbe8d460579ac5bf0138e3c17e28c9db2817c022b3e61b99e141327728904289a57f12956b9ace885e0e35fc9d8a298  firmware-oneplus-msm8998-9.0.11.zip"
