pkgname=firmware-oneplus-msm8998
pkgver=10.0.1
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

sha512sums="e61fbfe1c3821308a182a8c6f00db816e8e8dd7b7ed2aaca89e5b59d04e2d924b7a1259976ed92a8a1dd018ceb217788a6a6d2ec723110425769dfb7b0f35e0c  firmware-oneplus-msm8998-10.0.1.zip"
